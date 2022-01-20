---
title: "URL Shortener and Redirector web part"
menuTitle: "Overview"
date: 2022-01-10
draft: false
---
{{< rawhtml >}}
    <!-- first section -->
    <div style="display:flex;">
        <div style="text-align:center;">
            <h3>Overview</h3>
            <figure>
                <a href="/images/Overview.png" data-featherlight="image">
                    <img src="/images/Overview.png" style="width:90%;"/>
                </a>
            </figure>
        </div>
        <div style="text-align:center;">
            <h3>Demo</h3>
            <figure>
                <a href="/images/Overview.gif" data-featherlight="image">
                    <img src="/images/Overview.gif" style="width:87%;"/>
                </a>
            </figure>
        </div>
    </div>
    <hr style="clear:both;">
    <!-- other sections -->
    <div style="max-width:56em">
        <!-- slide 1 -->
        <div class="imageText">
            <p>The web part has 2 modes:</p>
            <p>Mode 1: If you open the SharePoint page that contains the web part, it starts in URL shortening mode.</p>
        </div>
        <figure class="right600">
            <a href="/images/01.png" data-featherlight="image">
                <img src="/images/01.png" />
            </a>
        </figure>
        <div class="imageText">
            <p>In URL shortening mode, you have two Features: Shorten a new URL and find an existing URL in the database.</p>
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
        <hr style="clear:both;">
        <!-- slide 2 -->
        <div class="imageText">
            <p>Mode 2: If you open the page with an Id, it starts in redirecting mode.</p>
        </div>
        <figure class="right600">
            <a href="/images/03.png" data-featherlight="image">
                <img src="/images/03.png" />
            </a>
        </figure>
        <div class="imageText">
            <p>In redirecting mode, you have one feature: The URL with an Id is the shortened URL, which will redirect to the original URL stored in the database.</p>
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
        <!-- slide 3 -->
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
            <p>1. Enter an input URL</p>
            <p>2. Click "Shorten and add to list"</p>
            <p>3. Get the output URL</p>
        </div>
        <hr style="clear:both;">
        <!-- slide 4 -->
        <div class="imageText">
            <p>Option 2: Shorten a URL with specific Id</p>
        </div>
        <figure class="right600">
            <a href="/images/06.png" data-featherlight="image">
                <img src="/images/06.png" />
            </a>
        </figure>
        <div class="red">
            <p>1. Enter an input URL</p>
            <p>2. Enter an Id</p>
            <p>3. Click "Shorten and add to list"</p>
            <p>4. Get the output URL</p>
        </div>
        <hr style="clear:both;">
        <!-- slide 5 -->
        <div class="imageText">
            <p>The second feature in URL shortening mode is to find an existing Id in the database.</p>
            <p>Find an existing URL</p>
        </div>
        <figure class="right600">
            <a href="/images/07.png" data-featherlight="image">
                <img src="/images/07.png" />
            </a>
        </figure>
        <div class="red">
            <p>1. Enter an input Id</p>
            <p>2. Click "Find URL"</p>
            <p>3. Get the output URL</p>
        </div>
    </div>
{{</rawhtml >}}
