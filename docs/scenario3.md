[Home](README.md) | 
[Scenario 1](scenario1.md) |
[Scenario 2](scenario2.md) |
[Scenario 3](scenario3.md) |
[CLI commands](cli-commands.md) 


# Scenario 3 - Interacting with the page before screenshots

Sometimes we might need to interact with the page before we take a screenshot. 
For example on our demo site we might want to click the expand, or on another recipe.

To do this we can export a function that has browser object passed in. 

There is already a folder `scripts` that contains a function that will click on an element.

lets create a new scenario with an onReady field and link it to our click script

    "scenarios": [{
            "url": "http://cookingapp:3000",
            "label": "recipe",
            "viewports": [
                {"height": 1000, "width": 1024, "label": "large"}
            ],
            "wait": 2000
            "removeSelectors": [".eww-a-bug"]
        },
        {
            "url": "http://cookingapp:3000",
            "label": "show-more-recipes",
            "onReadyScript": "./scripts/click.js",
            "viewports": [
                {"height": 1000, "width": 1024, "label": "large"}
            ],
            "wait": 2000
            "removeSelectors": [".eww-a-bug"]
        }]


Now lets change our click script to click on the recipe show me more

    vi scripts/click.js
--------------
    async function clickElement (browser, By) {
        await browser.findElement(By.css(".show-me-more")).click();
    };

    module.exports = clickElement;
---------------
    :wq

--------------
    ayespy snap --config ayespy-config.json --browser firefox 


lets check that our new scenario works by looking at the image 
`<your-animal>.devopsplayground.com/latest/show-more-recipes-large.png`

    ayespy update-baseline --config ayespy-config.json --browser firefox
    ayespy snap --config ayespy-config.json --browser firefox 
    ayespy compare --config ayespy-config.json --browser firefox 

-------

    info [configValidator] : Config validated ✅
    info [comparer] : ✅ Passed: recipe-large
    info [comparer] : ✅ Failed: show-more-recipes-large
    info [createDiffs] : Diff generated for show-more-recipes-large
    info [Reporter] :
    info [Reporter] :       AyeSpy
    info [Reporter] : ---------------------
    info [Reporter] :
    info [Reporter] : Scenarios Passed: 2
    info [Reporter] : Scenarios Failed: 0
    info [Reporter] :
    info [Reporter] : ---------------------
    info [Reporter] :
