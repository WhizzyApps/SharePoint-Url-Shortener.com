---
title: "Version 1.0.0"
date: 2022-01-20
draft: false
weight: 99
year: 2021
---
Karsten Held, Samuel Gross, 20.01.2022

### Web part modes
{{< rawhtml >}}
    <!-- other sections -->
    <div style="max-width:56em">
        <!-- slide 1 -->
        <figure>
            <a href="/images/Overview.png" data-featherlight="image">
                <img src="/images/Overview.png" style="width:90%;"/>
            </a>
        </figure>
        <div>The web part behaves differently, depending on the URL of the SharePoint page that contains the web part. The URL of the page has the following scheme: </div> 
        <code style>https://[TENANT].sharepoint.com/sites/[SITE]/SitePages/[PAGE].aspx</code>
        </br>
        <div style="display: inline">Example:</div>
        <code>https://whizzyapps.sharepoint.com/sites/test/SitePages/test.aspx</code>
        <figure class="center600">
            <a href="/images/01.png" data-featherlight="image">
                <img src="/images/01.png" />
            </a>
        </figure>
        <div>In this case the web part apprears in the URL shortener mode. </div>
        <div>If the URL has additionally an Id at the end, it appears in redirector mode. The URL with Id has the following scheme:</div>
        <code>https://[TENANT].sharepoint.com/sites/[SITE]/SitePages/[PAGE].aspx?$id=[ID]</code>
        </br>
        <div style="display: inline">Example:</div>
        <code>https://whizzyapps.sharepoint.com/sites/test/SitePages/test.aspx?$id=123abc</code>
        <figure class="center600">
            <a href="/images/03.png" data-featherlight="image">
                <img src="/images/03.png" />
            </a>
        </figure>
        <h4>URL shortener mode</h4>
        <div class="imageText">
            <p>In URL shortener mode, you have two features: Shorten a new URL and find an existing URL in the database.</p>
        </div>
        <figure class="right600">
            <a href="/images/02.png" data-featherlight="image">
                <img src="/images/02.png" />
            </a>
        </figure>
        <div class="red">
            <p>Feature 1: Shorten a URL</p>
            <p>Feature 2: Find an existing URL</p>
        </div>
        <h4>Redirector mode</h4>
        <div class="imageText">
            <p>In redirector mode, you have the third feature: The URL with an Id is the shortened URL, which will redirect to the original URL stored in the database.</p>
        </div>
        <figure class="right400">
            <a href="/images/04.png" data-featherlight="image">
                <img src="/images/04.png" />
            </a>
        </figure>
        <div class="red">
            <p>Feature 3: Redirecting a shortened URL</p>
        </div>
        <hr style="clear:both;">
{{</rawhtml >}}
### Web part features
{{< rawhtml >}}
        <!-- slide 2 -->
        <h4>Feature 1: Shorten a URL</h4>
        <p>The web part will shorten a URL of your choice. You enter the long URL and recieve the shortened URL, which is the URL of the web part page with an Id at the end.</p>
        <div class="imageText">
            <p>
                <div>To shorten a URL, you have to options:</div>
                <div>1) You only need to enter the input URL and the web part will generate the Id for the output URL.</div>
                <div>2) Besides the input URL, you can enter a specific Id to be used in the output URL.</div>
            </p>
            <p>Option 1: Shorten a URL with a generated Id</p>
        </div>
        <figure class="right600">
            <a href="/images/05.png" data-featherlight="image">
                <img src="/images/05.png" />
            </a>
        </figure>
        <div class="red">
            <p>1. Enter a URL in the "Input URL" text box.</p>
            <p>2. Click "Shorten and add to list".</p>
            <p>3. Find the shortened URL in the "Output URL" text box.</p>
        </div>
        <div class="imageText">
            <p>Option 2: Shorten a URL with specific Id</p>
        </div>
        <figure class="right600">
            <a href="/images/06.png" data-featherlight="image">
                <img src="/images/06.png" />
            </a>
        </figure>
        <div class="red">
            <p>1. Enter a URL in the "Input URL" text box.</p>
            <p>2. Enter an Id in the text box "I have an Id".</p>
            <p>3. Click "Shorten and add to list".</p>
            <p>4. Find the shortened URL in the "Output URL" text box.</p>
        </div>
        <hr style="clear:both;">
        <!-- slide 3 -->
        <h4>Feature 2: Find an existing URL</h4>
        <div class="imageText">
            <p>The second feature in URL shortener mode is to find an existing Id in the database.</p>
        </div>
        <figure class="right600">
            <a href="/images/07.png" data-featherlight="image">
                <img src="/images/07.png" />
            </a>
        </figure>
        <div class="red">
            <p>1. Enter an Id in the "Input Id" text box.</p>
            <p>2. Click "Find URL".</p>
            <p>3. Find the shortened URL in the "Output URL" text box.</p>
        </div>
        <hr style="clear:both;">
        <!-- slide 4 -->
        <h4>Feature 3: Redirecting a shortened URL</h4>
        <div class="imageText">
            <p>If you open the URL of the web part with an Id at the end, the web part will recognize the Id in the URL and start in redirector mode. It will search for the Id in the database and open the associated target URL automatically. This procedure is called redirecting a URL.</p>
        </div>
        <p>Open the URL of the web part with Id (=shortened URL)</p>
        <figure class="center600">
            <a href="/images/03.png" data-featherlight="image">
                <img src="/images/03.png" />
            </a>
        </figure>
        <p>The web part redirects to the target URL. Depending on the loading time of the sites, the web part will appear shortly as:</p>
        <figure class="center400">
            <a href="/images/04.png" data-featherlight="image">
                <img src="/images/04.png" />
            </a>
        </figure>
    </div>
    <hr style="clear:both;">
{{</rawhtml >}}

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
