---
title: "Version 1.0.0"
date: 2022-01-10
draft: false
weight: 99
year: 2021
---
Karsten Held, Samuel Gross, 20.01.2022

### Web part modes

{{< rawhtml >}}
<div style="overflow-wrap: normal;">
{{</ rawhtml >}}

1. **URL shortener mode** 

    - Open the page that contains the web part. 

    {{< figure src="/images/01.png" class="center600">}}

    - The web part starts in "URL shortener mode".

    {{< figure src="/images/c.png" class="center600">}}

      
2. **URL redirector mode** 

    - Open a shortened URL (containing an Id).

    {{< figure src="/images/03.png" class="center600">}}

    - The web part starts in "Redirector mode".

    {{< figure src="/images/04.png" class="center400">}}

### Web part features

In URL shortening mode, you have two Features: Shorten a new URL and find an existing URL in the database.

- 1. Shorten a URL
- 2. Find an existing URL

{{< figure src="/images/02.png" class="center600">}}

{{< rawhtml >}} <div class="imageText"></div> {{</rawhtml >}}

In redirecting mode, you have one feature: the URL with an Id is the shortened URL, which will redirect to the original URL stored in the database.

- 3. Redirecting a shortened URL
    
{{< figure src="/images/04.png" class="center400">}}

#### Feature 1: Shorten a URL

To shorten a URL, you have two options:

**Option 1:** Shorten a URL with a generated Id

You only need to enter the input URL and the web part will generate the Id for the output URL.
The web part stores the Id and the target URL in a database, which is a SharePoint list. This list must be created in the edit mode of the web part.

- 1. Enter an input URL
- 2. Click "Shorten and add to list"
- 3. Get the output URL

{{< figure src="/images/05.png" class="center600">}}

**Option 2:** Shorten a URL with specific Id

Besides the input URL, you can enter a specific Id to be used in the output URL.

- 1. Enter an input URL
- 2. Enter an Id
- 3. Click "Shorten and add to list"
- 4. Get the output URL

{{< figure src="/images/06.png" class="center600">}}

#### Feature 2: Find an existing URL

The second feature in URL shortening mode is to find an existing Id in the database.

Find an existing URL

- 1. Enter an input Id
- 2. Click "Find URL"
- 3. Get the output URL

{{< figure src="/images/07.png" class="center600">}}

#### Feature 3: Redirect a shortened URL

In **redirecting mode**, you have the third feature: The URL with an Id is the shortened URL, which will redirect to the original URL stored in the database.

- Open page of web part with Id (=shortened URL)

{{< figure src="/images/03.png" class="center600">}}

- The web part recognizes the Id in the URL, looks in the database for the target URL and redirects the user. Depending on the loading time of the sites, the web part will appear shortly as:

{{< figure src="/images/04.png" class="center400">}}

### Web part configuration 

  To configure the webpart, edit page, then edit web part. The web part "property pane" will blend in on the right. 

**About the web part**

  {{< figure src="/V1.0.0/images/01.png" class="right250" >}}

- Version number
- Build time stamp
- Link for documentation

Note: You need to be site owner or site admin to be able to configure the web part, otherwise the options will be disabled.

**Create new URL lookup list**

The database used by the web part is a SharePoint list, that stores the Ids of the shortened URLs and the target URLs.

You can create such a list:

- Enter the desired name.
- Click "Create".
- A message will be displayed if it was successful.

When you deploy the web part the first time, you need to create a lookup list.

You can have multiple lists, for example if you want to deploy the web part on multiple pages on the site collection.

**Select URL lookup list**

In the dropdown menu will be displayed all user created lists from the site collection. 

By clicking "Check list" it will be verified if the list contains the necesary columns with the names "Title", "Key", "TargetUrl" and if they are of the right type. 

**Set length of generated Id**

If you use the feature of the web part of shortening a URL with the option to generate an Id, the generated Id will initially have the length of 5 digits. You can choose a length between 4 and 16 digits.
