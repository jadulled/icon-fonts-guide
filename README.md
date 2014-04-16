# Icon fonts guide

## Table of contents

- [Goals](#goals)
- [Packages](#packages)
    - [Full package](#full-package)
    - [Component package](#component-package)
    - [Custom package](#custom-package)
- [How to use in your project](#how-to-use-in-your-project)
- [Cross domain workaround for @font-face and Firefox](#cross-domain-workaround-for-font-face-and-Firefox)

## Goals
This brief document seeks to **optimize the use of icons**, make easier their implementation and improve the scalability of each project. Its main goal is that **each project uses only the icons they really need**.

## Packages
Following this goals, the icon library was reviewed and three different packages were arranged:

### 1. Full package

Includes all the icons that we use in MercadoLibre. Most of them are courtesy of [Font Awesome](http://fortawesome.github.io/Font-Awesome/cheatsheet/) however are a few exceptions: 

- `icon-user` and `icon-users` are from **MFG Labs** library.
- `icon-offical-store`, `icon-card`, `icon-cash`, `icon-motorcycle` and `icon-trash` are custom so you must import their corresponding **SVG file** provided in this repo. To do this, simply drag and drop your files into [Fontello](http://www.fontello.com). 

You can use the full package from:
- [Chico UI CSS](http://static.mlstatic.com/org-img/ch/ui/1.1.1/index.html) through `ch-icon-*` classname.
- Standalone from CDN (Not available yet):
    - http://static.mlstatic.com/org-img/ch/assets/0.4/icons.eot
    - http://static.mlstatic.com/org-img/ch/assets/0.4/icons.svg
    - http://static.mlstatic.com/org-img/ch/assets/0.4/icons.ttf
    - http://static.mlstatic.com/org-img/ch/assets/0.4/icons.woff

### 2. Component package

Includes only the icons that a particular component needs. Eg.: Navigation Component (header + footer), Feedback Component, Reputation Component, etc.

You can find component packages on each component implementation.

### 3. Custom package

Includes only the icons that a particular project needs. You can create your own package following this simple steps:

1. Go to [Fontello](http://www.fontello.com).
2. Choose the icons you need from the list or include your own SVGs files provided in this repo.
3. Don't forget to name your font and to name your custom SVG files.
4. Finally, **download** your font and [include it in your project](#how-to-use-in-your-project).

## How to use in your project

1. Upload the `.eot`, `.svg`, `.ttf` and `.woff` files to a folder on your project.
2. Make sure these files are served up [supporting cross domain workarounds](#cross-domain-workaround-for-font-face-and-Firefox).
3. Import the font in your main stylesheet. In this example:
    - `buyingflow` is the name of the font.
    - `cho` is the namespace for the CSS selectors among the project.

    ```css
    @font-face {
        font-family: 'buyingflow';
        src: url('buyingflow.eot?93575983');
        src: url('buyingflow.eot?93575983#iefix') format('embedded-opentype'),
           url('buyingflow.woff?93575983') format('woff'),
           url('buyingflow.ttf?93575983') format('truetype'),
           url('buyingflow.svg?93575983#fontello') format('svg');
        font-style: normal;
        font-weight: normal;
    }
```

4. Set default styling for your icons:
    
    ```css
    [class^='cho-icon-']:before,
    [class*=' cho-icon-']:before {
        display: inline-block;
        font-family: 'buyingflow';
        font-style: normal;
        font-variant: normal; /* For safety - reset parent styles, that can break glyph codes*/
        margin: 0 .2em;
        speak: none;
        text-align: center;
        width: 1em;
    }
    ```

5. Add the icons definition to your stylesheet. Fontello exports something like this:
    ```css
    .icon-user:before { content: '\e801'; }
    .icon-help-circled:before { content: '\e800'; }
    ```

    Make sure to add your project namespace:

    ```css
    .cho-icon-user:before {
        content: '\e801';
    }

    .cho-icon-help-circled:before {
        content: '\e800';
    }
    ```

6. Use the `<i>` tag for icons:

    ```html
    <p><i class="cho-icon-help-circled"></i> Help</p>
    ```

## Cross domain workaround for `@font-face` and Firefox

Firefox doesn't allow cross-domain fonts by default. This means the font must be served up from the same domain (and sub-domain) unless you can add an `Access-Control-Allow-Origin` header to the font.

More info [here](http://red-team-design.com/firefox-doesnt-allow-cross-domain-fonts-by-default/).

You can check if your files are served up with the header via terminal:
```
curl -v 'url-of-font-file.woff'
```
