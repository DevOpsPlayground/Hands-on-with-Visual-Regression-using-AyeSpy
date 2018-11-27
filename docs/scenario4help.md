


### Spoilers alert



If you're struggling with flake, it looks like it might be down to two things

- not waiting long enough to allow the menu to fully render

    until the menu is fully rendered there is still some opacity so menu gradient between images may not always match


- when clicking on the burger menu sometimes profile menu is highlighted.
Maybe we need to move the mouse away in our on before script file?
try something like this to move the element away 
```
    await browser.findElement(By.css('.show-me-more')).then(elem => 
        browser.actions().move({origin: elem}).perform())
```
