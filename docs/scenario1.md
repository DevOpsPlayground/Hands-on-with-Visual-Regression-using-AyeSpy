[Home](../README.md) | 
[Scenario 1](scenario1.md) |
[Scenario 2](scenario2.md) |
[Scenario 3](scenario3.md) |
[Scenario 4](scenario4.md) |
[Cheatsheet](cheatsheet.md) |
[CLI commands](cli-commands.md) 

# Scenario 1 - Comparing the Homepage

A great starting place for any tester!

The selenium grid, demo test site, and report are already being ran on our remote machine so all we need to do - is set up our aye spy config to take a snapshot of the homepage.

Lets inspect what the files in our ayespy directory

    cd ayespy 
    ls

The template ayespy-config.json has already been set up for us! 
Lets take a look

    cat ayespy-config.json
-------------
    {
        "gridUrl": "http://localhost:4444/wd/hub",
        "baseline": "./baseline",
        "latest": "./latest",
        "generatedDiffs": "./generatedDiffs",
        "report": "./reports",
        "scenarios": [{
            "url": "http://cookingapp:3000",
            "label": "homepage",
            "viewports": [{"height": 2400, "width": 1024, "label": "large"}]
        }]
    }



Looks good! 
Lets get some images 

    ayespy snap --config ayespy-config.json --browser firefox 


To view the file you can see it from your browser
`<YOURANIMAL>.devopsplayground.com/latest/homepage-large.png

lets update the baseline

    ayespy update-baseline --config ayespy-config.json --browser firefox

and run another snap

    ayespy snap --config ayespy-config.json --browser firefox

lets see if when we run the comparison if that passes?

    ayespy compare --config ayespy-config.json --browser firefox


If you're lucky it might have passed, but if you're unlucky it may have failed :(

Lets look at the report and find out why

in your browser navigate to
    
    <your-animal>.devopsplayground.com


Looks like we have some dynamic content that might not always display. On a real site this could be something like an advert, video, carousel or anything else not static.



![](/images/bug-report.png)


We should remove it by editing out config and making use of remove selectors

    vi ayespy-config.json

----------------------
    "scenarios": [{
            "url": "http://cookingapp:3000",
            "label": "homepage",
            "viewports": [{"height": 1000, "width": 1024, "label": "large"}],
            "removeSelectors": [".eww-a-bug"]
        }]

------------
    :wq

Lets rerun aye spy with our latest config. Please bare in mind, if your baseline image has the dynamic element we will need to update your baseline too!

    info ayespy Logger Log level is info
    info [configValidator] : Config validated ✅
    info [comparer] : ✅ Passed: homepage-large
    info [Reporter] :
    info [Reporter] :       AyeSpy
    info [Reporter] : ---------------------
    info [Reporter] :
    info [Reporter] : Scenarios Passed: 1
    info [Reporter] : Scenarios Failed: 0
    info [Reporter] :
    info [Reporter] : ---------------------
    info [Reporter] :


