---
title: "API endpoints"
date: 2022-01-20
draft: false
weight: 02
---
Karsten Held, Samuel Gross, 20.01.2022

**Where does the data come from?**

The web part interacts with SharePoint REST API.

This page explains all endpoints used by the following methods: 

- A) SharePoint API get
- B) SharePoint API post

### A) SharePoint API **get** requests

#### Preparing web part

- To get access to the SharePoint API, SPFX needs the object spHttpClient from the web part context.
  - I.e. the get method is accessable like this: `this.context.spHttpClient.get()`
  - The context is accessible in the main *.ts file "UrlShortenerWebPart.ts". 
  - Put the context in the web part props: `context: this.context`, see below.
  
Example in src/webparts/urlShortener/UrlShortenerWebPart.ts file:
```
export default class UrlShortenerWebPart extends BaseClientSideWebPart<IUrlShortenerWebPartProps> 
{
    public render(): void {
        const element: React.ReactElement<IUrlShortenerProps> = React.createElement(
            UrlShortener,
            {
                context: this.context,
            }
        );
    }
}
```

- The web part props need to be declared in the interface file "IUrlShortenerWebPartProps.ts", see below:

Example in IUrlShortenerWebPartProps.ts
```
import { WebPartContext } from '@microsoft/sp-webpart-base';

export interface IUrlShortenerProps {
    context: WebPartContext;
}
```
- Then you can access the spHttpClient in the UrlShortenerWebPart.ts file within the web part props: `this.context.spHttpClient`, see below:

#### Example for API calls

Example function for Typescript-React in UrlShortenerWebPart.ts file:

``` 
import { SPHttpClient, ISPHttpClientOptions} from '@microsoft/sp-http';

export default class UrlShortenerWebPart extends BaseClientSideWebPart<IUrlShortenerWebPartProps> 
{
    // function for API call
    private async _spApiGet (url: string): Promise<object> 
    {
        const clientOptions: ISPHttpClientOptions = {
            headers: new Headers(),
            method: 'GET',
            mode: 'cors'
        };
        const response = await this.context.spHttpClient.get(this.context.pageContext.web.absoluteUrl + url, SPHttpClient.configurations.v1, clientOptions);
        const responseJson = await response.json();
        return responseJson;
    }
}
``` 

- The function is the same in a .tsx file like in the .ts file from above. The only difference is the access to the context. In the .ts file you use `this.context`. In the .tsx file you use `this.props.context`.

Example function for Typescript-React in UrlShortener.tsx file:
``` 
import { SPHttpClient, ISPHttpClientOptions} from '@microsoft/sp-http';

// main class in UrlShortener.tsx file
export default class SpoUrlShortener extends React.Component<IUrlShortenerProps, {}> 
{
    // function for API call
    private async _spApiGet (url: string): Promise<object> 
    {
        const clientOptions: ISPHttpClientOptions = {
            headers: new Headers(),
            method: 'GET',
            mode: 'cors'
        };
        const response = await this.props.context.spHttpClient.get(this.props.context.pageContext.web.absoluteUrl + url, SPHttpClient.configurations.v1, clientOptions);
        const responseJson = await response.json();
        return responseJson;
    }
}
```

Call _spApiGet(url) from another function with the parameter "url":

```
public async myFunction() {
  const url = "/_api/web/currentuser/isSiteAdmin";
  const response = await this._spApiGet(url);
  console.log(response);
}
```

#### Endpoints

All endpoints (URLs) use the site URL

- [SITE_URL] = ```https://[YOUR_TENANT].sharepoint.com/sites/[YOUR_SITE]```
- Example: ```https://myTenant.sharepoint.com/sites/mySite```
- For root site: ```https://myTenant.sharepoint.com```

Get current user permissions

- `[SITE_URL]/_api/web/currentuser/isSiteAdmin`
- `[SITE_URL]/_api/web/effectiveBasePermissions`

Get lists of site

- `[SITE_URL]/_api/web/lists`

Get specific list of site

- `[SITE_URL]/_api/web/lists/GetById('[LIST_ID]')`

Get items of list

- `[SITE_URL]/_api/web/lists/GetById('[LIST_ID]')/items`

Get fields of list

- `[SITE_URL]/_api/web/lists/GetById('[LIST_ID]')/fields`



### B) SharePoint API **post** requests

#### Basic function for API posts

- Create a function that can be reused for api posts with parameters "url" and "data".

Example function for Typescript-React in UrlShortenerWebPart.ts file:

``` 
import { SPHttpClient, ISPHttpClientOptions} from '@microsoft/sp-http';

export default class UrlShortenerWebPart extends BaseClientSideWebPart<IUrlShortenerWebPartProps> 
{
    private async _spApiPost (url: string, data): Promise<object> 
    {
        const clientOptions: ISPHttpClientOptions = {
            headers: {
                'Accept': 'application/json;odata=nometadata',
                'Content-type': 'application/json;odata=verbose',
                'odata-version': '',
            },
            body: data,
            mode: 'cors'
        };
        const response = await this.context.spHttpClient.post(this.context.pageContext.web.absoluteUrl + url, SPHttpClient.configurations.v1, clientOptions);
        const responseJson = await response.json();
        return responseJson;
    }
}
``` 

- The function is the same in a .tsx file like in the .ts file from above. The only difference is the access to the context. In the .ts file you use `this.context`. In the .tsx file you use `this.props.context`.

Example function for Typescript-React in UrlShortener.tsx file:

``` 
import { SPHttpClient, ISPHttpClientOptions} from '@microsoft/sp-http';

export default class SpoUrlShortener extends React.Component<IUrlShortenerProps, {}> 
{
    private async _spApiPost (url: string, data): Promise<object> 
    {
        const clientOptions: ISPHttpClientOptions = {
            headers: {
                'Accept': 'application/json;odata=nometadata',
                'Content-type': 'application/json;odata=verbose',
                'odata-version': '',
            },
            body: data,
            mode: 'cors'
        };
        const response = await this.props.context.spHttpClient.post(this.props.context.pageContext.web.absoluteUrl + url, SPHttpClient.configurations.v1, clientOptions);
        const responseJson = await response.json();
        return responseJson;
    }
}
``` 

#### Create a list

- Create a list by calling "_spApiPost(url, data)".
- url: `[SITE_URL]/_api/web/lists`
- The data contains the "type", "BaseTemplate", "Description" and the "Title".

Example function for Typescript-React in UrlShortenerWebPart.ts file:

``` 
import { SPHttpClient, ISPHttpClientOptions} from '@microsoft/sp-http';

// main class in UrlShortenerWebPart.ts file
export default class UrlShortenerWebPart extends BaseClientSideWebPart<IUrlShortenerWebPartProps> 
{
    // function to create list
    private async _createList (name:String) 
    {
        const url = '/_api/web/lists';
        const data = JSON.stringify({
            '__metadata': { 'type': "SP.List" },
            "BaseTemplate": 100,
            "Description": "URL lookup list for URL-shortener-web-part",
            "Title": name,
        });
        const response = await this._spApiPost(url, data);
        return response;
    }
}
```

Call _createList(name) from another function with the parameter "name".

```
public async myFunction() 
{
    const response = await this._createList ("MyListName");
    console.log(response);
}
```

#### Create a list field (column)

- Create a list by calling "_spApiPost(url, data)".
- url: `[SITE_URL]/_api/web/lists/GetByTitle('[YOUR_LIST]')/Fields`
- The data contains the following properties: "type", "Title", "StaticName", "FieldTypeKind", "Required", "EnforceUniqueValues", "Indexed"

Example function for Typescript-React in UrlShortenerWebPart.ts file:

``` 
import { SPHttpClient, ISPHttpClientOptions} from '@microsoft/sp-http';

// main class in UrlShortenerWebPart.ts file
export default class UrlShortenerWebPart extends BaseClientSideWebPart<IUrlShortenerWebPartProps> 
{
    // function to create field
    private async _createListField (listName:String, FieldName:String, FieldType:number, EnforceUniqueValues:boolean) 
    {
        const url = `/_api/web/lists/GetByTitle('${listName}')/Fields`;
        const data = JSON.stringify({
            '__metadata': { 'type': "SP.Field" },
            "Title": FieldName,
            "StaticName": FieldName,
            "FieldTypeKind": FieldType,
            "Required": "true",
            "EnforceUniqueValues": EnforceUniqueValues,
            "Indexed": EnforceUniqueValues,
        });
        return await this._spApiPost(url, data);
    }
}
```

Call _createListField(listName, FieldName, FieldType, EnforceUniqueValues) from another function with the parameters.

```
public async myFunction() 
{
    const response = await this._createListField("MyListName", "Key", 2, true);
    console.log(response);
}
```

#### Add field to view

- Create a list by calling "_spApiPost(url, data)".
- url: `[SITE_URL]/_api/web/lists/GetByTitle('[YOUR_LIST]')/Views/GetByTitle('All%20Items')/ViewFields/addViewField('[YOUR_FIELD]')`
- The data is empty.

Example function for Typescript-React in UrlShortenerWebPart.ts file:

``` 
import { SPHttpClient, ISPHttpClientOptions} from '@microsoft/sp-http';

// main class in UrlShortenerWebPart.ts file
export default class UrlShortenerWebPart extends BaseClientSideWebPart<IUrlShortenerWebPartProps> 
{
    // function to add field to default view
    private async _addFieldToView (listName:String, FieldName:String) 
    {
        // add Field to view
        const url = `/_api/web/lists/GetByTitle('${listName}')/Views/GetByTitle('All%20Items')/ViewFields/addViewField('${FieldName}')`;
        const response = await this._spApiPost(url, "");
        return response;
    }
}
```

Call _addFieldToView(listName, FieldName) from another function with the parameters.

```
public async myFunction() 
{
    const response = await this._addFieldToView ("MyListName", "MyFieldName");
    console.log(response);
}
```

#### Create a list item

- Create a list item by calling "_spApiPost(url, data)".
- "url": `7_api/web/lists/GetById('[LIST_ID]')/items` 
- "data" contains the following properties: "type", "Title", "Key", "Url".
- Get the type of the list by api call: `this._spApiGet(url`) 
- with url: `/_api/web/lists/GetByTitle('${[LIST_NAME]}')?$select=ListItemEntityTypeFullName`
- "Title" and "Key" are in our case the same: the Id of the shortened URL.
- "Url" is in our case the target URL.

Example function for Typescript-React in UrlShortener.tsx file:

``` 
import { SPHttpClient, ISPHttpClientOptions} from '@microsoft/sp-http';

// main class in UrlShortener.tsx file
export default class SpoUrlShortener extends React.Component<IUrlShortenerProps, {}> 
{
    // function to create list item
    private async _createListItem (listName:String, key:String, inputUrl:String) 
    {
        // get list type
        let getListResponse = await this._spApiGet(`/_api/web/lists/GetByTitle('${listName}')?$select=ListItemEntityTypeFullName`); 
        let type = getListResponse["ListItemEntityTypeFullName"];
        
        // post list item
        const url = `/_api/web/lists/GetByTitle('${listName}')/items`;
        const data = JSON.stringify({
            '__metadata': { 'type': type },
            "Title": key,
            "Key": key,/* 
            "TargetUrl": 
            {
                '__metadata': { 'type': 'SP.FieldUrlValue' },
                'Url': inputUrl,
            }, */
        });
        return await this._spApiPost(url, data);
    }
}
```

Call _createListItem(listName, type, key, inputUrl) from another function with the parameters.

```
public async componentDidMount() 
{
    const response = await this._createListItem("MyListName", "123abc", "https://google.com");
    console.log(response);
}
```