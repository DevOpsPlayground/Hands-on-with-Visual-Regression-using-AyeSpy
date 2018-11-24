[Home](README.md) | 
[Scenario 1](scenario1.md) |
[Scenario 2](scenario2.md) |
[Scenario 3](scenario3.md) |
[CLI commands](cli-commands.md) 

# Scenario 2 - Running across various breakpoints

It's rare that our site will only be accessed in one breakpoint. Lets increase our coverage and confidence in our application by covering multiple breakpoints.

    vi ayespy-config.json

----------------------
    "scenarios": [{
            "url": "http://cookingapp:3000",
            "label": "homepage",
            "viewports": [
                {"height": 1000, "width": 1024, "label": "large"}
                {"height": 1000, "width": 550, "label": "small"},
            ],
            "wait": 2000
            "removeSelectors": [".eww-a-bug"]
        }]

------------
    :wq


So lets run ayespy with our new breakpoints

    ayespy snap --config ayespy-config.json --browser firefox 

Now that we have new images we will need to once again update the baseline

    ayespy update-baseline --config ayespy-config.json --browser firefox


and to run the report

    ayespy compare --config ayespy-config.json --browser firefox


