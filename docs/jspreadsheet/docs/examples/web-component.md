title: Spreadsheet Web Component with Jspreadsheet  
keywords: Jexcel, JavaScript, JavaScript plugin, web component, spreadsheet, data grid, table, Excel-like grid, data tables, data visualization  
description: Learn how to use Jspreadsheet CE to create a fully functional spreadsheet as a web component for your applications.

# Spreadsheet Web Component

Easily create a spreadsheet web component using Jspreadsheet CE for seamless integration into your web applications.

```html
<html>
<script src="https://bossanova.uk/jspreadsheet/v5/jspreadsheet.js"></script>
<script src="https://jsuites.net/v5/jsuites.js"></script>

<j-spreadsheet />

<script>
class Jspreadsheet extends HTMLElement {
    constructor() {
        super();
    }

    init(o) {
        // Shadow root
        const shadowRoot = this.attachShadow({mode: 'open'});

        // Style
        const css = document.createElement('link');
        css.rel = 'stylesheet';
        css.type = 'text/css'
        css.href = 'https://cdn.jsdelivr.net/npm/jspreadsheet-ce@5.0.0-beta.3/dist/jspreadsheet.min.css';
        shadowRoot.appendChild(css);

        const cssJsuites = document.createElement('link');
        cssJsuites.rel = 'stylesheet';
        cssJsuites.type = 'text/css'
        cssJsuites.href = 'https://cdn.jsdelivr.net/npm/jsuites/dist/jsuites.min.css';
        shadowRoot.appendChild(cssJsuites);

        const cssMaterial = document.createElement('link');
        cssMaterial.rel = 'stylesheet';
        cssMaterial.type = 'text/css'
        cssMaterial.href = 'https://fonts.googleapis.com/css?family=Material+Icons';
        shadowRoot.appendChild(cssMaterial);

        // JSS container
        var container = document.createElement('div');
        shadowRoot.appendChild(container);

        // Properties
        var toolbar = this.getAttribute('toolbar') == "true" ? true : false;

        // Create jexcel element
        this.el = jspreadsheet(container, {
            tabs: true,
            toolbar: toolbar,
            root: shadowRoot,
            worksheets: [{
                filters: true,
                minDimensions: [6,6],
            }],
        });
    }

    connectedCallback() {
        this.init(this);
    }

    disconnectedCallback() {
    }

    attributeChangedCallback() {
    }
}

window.customElements.define('j-spreadsheet', Jspreadsheet);
</script>
</html>
```