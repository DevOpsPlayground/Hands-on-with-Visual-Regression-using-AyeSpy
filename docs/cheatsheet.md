[Home](README.md) | 
[Scenario 1](docs/scenario1.md) |
[Scenario 2](docs/scenario2.md) |
[Scenario 3](docs/scenario3.md) |
[CLI commands](docs/cli-commands.md) 

    {
        "gridUrl": "http://selenium-grid:4444/wd/hub",
        "baseline": "./baseline", 
        "latest": "./latest",
        "generatedDiffs": "./generatedDiffs",
        "report": "./reports",
        "remoteBucketName": "aye-spy-example", 
        "remoteRegion": "eu-west-1",
        "scenarios": [
        {
            "url": "http://thetimes.co.uk/",
            "label": "homepage",
            "cropToSelector": ".flickity-slider", // crop the screenshot to a specific selector
            "removeSelectors": ["#ad-header"], // remove elements that are not static on refresh such as adverts
            "viewports": [{"height": 2400, "width": 1024, "label": "large"}],
            "cookies": [
            {
                "name": "cookie_name",
                "value": "cookie_value"
            }
            ],
            "waitForSelector": "#section-news", // explicitly wait for a selector to be visible before snap
            "onReadyScript": "./scripts/clickSelector.js", // run a script before snap
            "wait": 2000 // implicitly wait before taking a snap
        }]
    }
