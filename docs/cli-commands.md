[Home](README.md) | 
[Scenario 1](docs/scenario1.md) |
[Scenario 2](docs/scenario2.md) |
[Scenario 3](docs/scenario3.md) |
[CLI commands](docs/cli-commands.md) 


## Take the latest screenshots for comparison

    ayespy snap --browser firefox --config config.json

## Set your latest screenshots as the baselines for future comparisons

    ayespy update-baseline --browser firefox --config config.json

## Run the comparison between baseline and latest

    ayespy compare --browser firefox --config config.json

## Run a single scenario based on label name

    ayespy snap --browser firefox --config config.json --run "scenarioName"
