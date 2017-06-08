# Local modules

---
### Preventing classname bleed-out

By default, class styles in your CSS/SASS/LESS files will be exported as _local_ modules. Class names will be hashed to prevent bleeding out to your global namespace, and those same class names are then injected into the React code that is bundled for you. e.g:

![CSS local classnames](img/classnames.png)

The benefit to this is tight coupling of style logic with your components.  You don't have to worry that you've used globally unique class names, because Webpack will transpile your names into garbled, hashed versions to avoid conflicts.

> If you want to _avoid_ outputting local classnames, check out [global classnames](globals.md) syntax.
