---
title: "Deployment instructions"
date: 2021-12-01
draft: false
weight: 01
---
Karsten Held, Samuel Gross, 01.12.2021


### 1) Download

- Download the zipped web part package file **url-shortener-and-redirector-webpart.sppkg** from GitHub:
{{< rawhtml >}}
    <a style="align-self: flex-start;" href="https://github.com/WhizzyApps/SPO-URL-Shortener-And-Redirector-Web-Part/releases">Latest release/</a>
    <a style="align-self: flex-start;" href="https://github.com/WhizzyApps/SPO-URL-Shortener-And-Redirector-Web-Part/releases" target="_blank">All releases</a>
{{</ rawhtml >}}
- Unzip the SPPKG file. Do not rename this file. The filename has to match the package name.


### 2) Deployment to the global app catalog

#### A) Go to your App Catalog site

- Check if you have an App Catalog site by navigating to it. If you don't know the URL of your App Catalog site, follow one of these steps:
- Option a) Use this link: 
`https://[YOUR_TENANT]-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement/view/ALL%20SITES`

- Option b) Navigate to the SharePoint company App Catalog: 
  - Go to the Microsoft 365 admin center > Show all > SharePoint > Sites > Active sites
  - In the "Template" column, filter by "App Catalog Site" and click on the App Catalog Site URL.

![](/Deployment/images/04.png)

- If you don't have an App Catalog, make sure to create one first under point B). Else, go to point C).

#### B) Create an App Catalog site - optional


- In the SharePoint admin center, navigate through More features > Apps > open

![](/Deployment/images/01.png)

- Go to App Catalog:

![](/Deployment/images/02.png)

- Create a new app catalog site > OK:

![](/Deployment/images/03.png)

- On the next site, fill out the data > OK

#### C) Deploy the webpart to the global app catalog 

- In the App Catalog Site click on "Apps for SharePoint" > New > Choose Files > select the downloaded **url-shortener-and-redirector-webpart.sppkg** file > OK > then click "Deploy".

![](/Deployment/images/05.png)


- After the deployment, make sure the file is checked in. If you see an icon with a small green arrow you need to manually check the file in: Click the ellipsis (…) icon of the file > … > Advanced > Check In > OK

![](/Deployment/images/06.png)


### 3) Deployment to a site collection app catalog

- Navigate to the site collection you want to deploy the web part. Click on New > App

![](/Deployment/images/08.png)

- Go to "From Your Organization" > Add "URL Shortener and Redirector web part".

![](/Deployment/images/09.png)


### 4) Add webpart to your site

- On your site, in the upper right corner, click on "Edit".

![](/Deployment/images/10.png)


- Click on the "plus" in the section where you want to place the web part. 
- Type "url" and click on the icon of the "URL Shortener and Redirector". 

![](/Deployment/images/11.png)

- The web part will appear with disabled fields, because we need to set a lookup list first.

![](/Deployment/images/12.png)

### 5) Create and set lookup list

On first deployment, you need to create and set a lookup list.

1. Click "Edit" to edit web part properties. The "Property pane" will blend in on the right.
2. To create a new list, enter the desired name.
3. Click "Create".
4. A Message appears that the list was created successfully. Click "OK".

![](/Deployment/images/13.png)

Set the lookup list:

1. Select the list from the dropdown menu
2. The web part will be enabled immediately.
3. Click "Republish".

![](/Deployment/images/14.png)
