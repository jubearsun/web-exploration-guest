# Intro to Responsive Web Design

## Useful Sublime Things

* [Sublime Package Manager](https://packagecontrol.io/installation)

* [Emmet](http://emmet.io/download/)
  * Install through Sublime Package Control or on their website
  * Has support for other text editors (not vim though sorry)! Personally only used on Sublime but you can try it out if you use something else
  * In Sublime: ```cmd + shift + P``` to open Package Control
  * Choose ```Package Control: Install Package```
  * Search ```Emmet```

* [FakeImg](http://fakeimg.pl/)
  * Install through Sublime or on their website
  * In Sublime: ```cmd + shift + P``` to open Package Control
  * Choose ```Package Control: Install Package```
  * Search ```FakeImg Image Placeholder Snippet```

## What is Responsive Web Design?

Responsive web design aims to provide optimal interaction and viewing experience.  This is important because many users are now using their mobile phones or tablets to browse websites.  It is in your best interest to maximize their viewing pleasure -- no one wants to visit a broken website!

## Head Tags

The information between ```<head>``` tags contain information for the browser on how to render your website (meta tags) and links to stylesheets for your page.

```
<meta name="viewport" content="width=device-width, initial-scale=1">
```

This tells the browser to set the width of the page to the width of your device, which allows media queries to help with responsive design.

We also link our CSS stylesheet in the head tag so our HTML page knows where to look for styling.  Right above it, we link a CDN to ```normalize.css```.  Normalize 'resets' all styles on the web page.  Since all browsers have their own preset styles, for compatibility across different browsers we want to set the styles to a baseline so your website will look the same on Firefox, Chrome, Safari, etc...

## Body Tags

Where you put your code! :)

## CSS Best Practices

The given code in ```style.css``` sets a preferred base styling.  Don't worry if you don't fully understand this yet, but a quick rundown:

* ```*``` in CSS selects all HTML elements
* ```::before``` and ```::after``` are pseudo elements, which basically allows you to insert content onto a page from CSS before and after an HTML element
* We want to set all HTML elements and their pseudo elements' box-sizing to border box -- box-sizing tells the browser what width and height should include (refer to CSS box model)
* We want all elements to have position relative, which means that they will be positioned relative to their normal position (the default position is static, which means elements are positioned based on the normal flow of the page, and elements with position static will not be affected by top, bottom, left and right properties)
