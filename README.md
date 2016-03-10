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

## Square Grid Math

We can specify width in percentage.  Recall that width percentage is percent of the parent element width -- so your parent element is 100% width relative to the child.  In our example we wanted three grid-items per row, so we would specify each grid-item to have a width of 33%.

But wait, that leaves no space for gutters!  In an example with 3 grid-items per row, we want 2 gutters with widths of 2% each.  Therefore our grid-items are actually going to be (100 - 2 * 2)/3 = 32% width.

Height is a little bit trickier.  Recall that height percentage is also percent of the parent element height, but we never specified a height for the parent, our grid-items will end up defaulting to 0 height if we specify a height in percentage.  Therefore we need to figure out height in terms of viewport width, or vw.  We need to find the exact vw of our ```grid-item``` widths and put that in as the height.

Recall that 1% page width = 1 vw.

We have:
1. A padding of 2% on the page-container (4% total width-wise)
2. A grid-wrapper with 75% width of the parent (page-container)
3. grid-items with 32% width of their parent (grid-wrapper)

...which gives us (100-2(2)) * 0.75 * 0.32 = 23.04vw for the height of the grid-items.

## nth-child

In a grid with three grid-items per row, you don't want the last item in the row to have a margin-right because there is nothing to its right!  Here is where the ```nth-child``` selector comes in.

```.grid-item:nth-child(3n)``` selects every third child of class ```grid-item```, and we can set the ```margin-right``` to 0 within it.

When you do media queries, remember to undo the nth-child!  For example, when we only wanted 2 ```grid-item``` per row, we had to reset every third child to have a ```margin-right``` of 2% again before setting every second child to have a ```margin-right``` of 0.

## Media Queries

```@media (max-width: 500px)``` tells your browser to apply these styles when screen width is less than or equal to 500px.  Usually you put media queries at the bottom of the page, in descending order of width.  This is because CSS stands for "Cascading Stylesheets", which means that styles at the bottom of the page will take precedent over the ones before it.
