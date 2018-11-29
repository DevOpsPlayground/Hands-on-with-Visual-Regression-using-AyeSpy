[Home](../README.md) | 
[Scenario 1](scenario1.md) |
[Scenario 2](scenario2.md) |
[Scenario 3](scenario3.md) |
[Scenario 4](scenario4.md) |
[Cheatsheet](cheatsheet.md) |
[CLI commands](cli-commands.md) 

# Scenario 2 - Running across various breakpoints

It's rare that our site will only be accessed in one breakpoint. Lets increase our coverage and our confidence in our application by covering multiple breakpoints.

    vi ayespy-config.json
    i

----------------------
    "scenarios": [{
            "url": "http://cookingapp:3000",
            "label": "homepage",
            "viewports": [
                {"height": 1000, "width": 1024, "label": "large"},
                {"height": 1000, "width": 550, "label": "small"}
            ],
            "removeSelectors": [".eww-a-bug"]
        }]

------------
    ESC
    :wq


So lets run ayespy with our new breakpoints

    ayespy snap --config ayespy-config.json --browser firefox 

Now that we have new images we will need to once again update the baseline

    ayespy update-baseline --config ayespy-config.json --browser firefox


and to run the report

    ayespy compare --config ayespy-config.json --browser firefox


    info ayespy Logger Log level is info
    info [configValidator] : Config validated ✅
    info [comparer] : ✅ Passed: homepage-large
    info [comparer] : ✅ Passed: homepage-small
    info [Reporter] :
    info [Reporter] :       AyeSpy
    info [Reporter] : ---------------------
    info [Reporter] :
    info [Reporter] : Scenarios Passed: 2
    info [Reporter] : Scenarios Failed: 0
    info [Reporter] :
    info [Reporter] : ---------------------
    info [Reporter] :
