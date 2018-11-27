[Home](README.md) | 
[Scenario 1](scenario1.md) |
[Scenario 2](scenario2.md) |
[Scenario 3](scenario3.md) |
[Scenario 4](scenario4.md) |
[Cheatsheet](cheatsheet.md) |
[CLI commands](cli-commands.md) 


# Scenario 4 - Down to you!

The last scenario is down to you to figure out!

Take a look at the [Cheatsheet](cheatsheet.md) to see the full list of the ayespy config.

We want to crop to just the burger menu list.

You will probably want to think about clicking on the burger menu first!

Feel free to use the nice ECSD folk around the room if you get stuck!

The selectors that you will be interested in are all here

    .the-hamburger-button 
    .eww-a-bug 
    .MuiPaper-elevation8-023  (the menu list)




If you need a hand scroll down to get the scenario robust!
.
.
.
.
.
.
.
.
.
.
.
.
Spoilers alert
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
.
If you're struggling with flake, it looks like it might be down to two things

- not waiting long enough to allow the menu to fully render

    until the menu is fully rendered the is still some opacity which so menu gradient may not always match


- when clicking on the burger menu sometimes profile menu is highlighted.
Maybe we need to move the mouse away in our on before script file?
try something like this to move the element away 
```
    await browser.findElement(By.css('.show-me-more')).then(elem => 
        browser.actions().move({origin: elem}).perform())
```
