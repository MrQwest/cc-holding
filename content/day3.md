---
layout: _main.njk
title: Day 3 - Getting responsive
---

So as I've just started getting some colours and some layouts down into my CSS file, now's a good time to look at going responsive.

## A bit of history

Back when I was more  involved in front-end code, *Mobile First* was one of the ways to tackle development; the other being Responsive/Adaptive Design.

The idea behind Mobile First being that you develop and code for the I guess, the worst case scenario and then add in code, functionality and flair as the device gets better. As the screen gets bigger, you can improve the layout or increase the type. As the connection gets quicker, you can load more images or higher resolution images and as the device gets more powerful, you can load in more function with JS.  Solid idea I think.

Responsive Design was almost the other way round where you'd design and build your site to suit the desired requirements. Responsive design allows the design to respond to the scenario and has the functionality coded in to cover these scenarios. Responsive design keeps the design fluid so it flows to the size of the screen and and moves elements around to suit the screen size; and as the screen size reduces, you can remove superfluous design detail.

Adaptive works similar to responsive where you design and build to suit the desired requirements but you set 'breakpoints', so creating several fixed layouts to suit mobile, tablet, desktops and above and as the page loads, it determines the specification of the device loading it and serves up the corresponding layout.

But that was then. I do want to explore more modern ways of being responsive but for now, I'll add in some media queries so that I can make the most of available screen real estate where needed.

## Media Queries

The Mozilla Developer Network (MDN) has a great resource and write up on [Media Queries]("https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries") and I thoroughly recommend you having a read for a deeper, more in depth look at what `Media Queries` can do.

For the moment, I'll be using media queries to define certain styles that should be applied if the device matches the query.

First job (and one I always forget) is to add the following tag to the head of your page or in our case, `_main.njk`

`<meta name="viewport" content="width=device-width, initial-scale=1.0">`

This tells the browser how to control the dimensions and scaling of the page.

And then we need to add media queries to our CSS file to change & resize elements based on our screen size. Simple media queries looks like this:

`@media (width <= 30em) { [your css goes here] }`

This lives within your `CSS` file. The `@media` portion tells your browser that we're looking at a query here. The proceeding bracketed statement, in this case `(width <= 30em)` provides the browser with a logical question. Is the width of the screen *less than or equal to* 30rem. If the result of this question is **true**, then the CSS within the braces, `{ ... }` gets applied to your page.

Now it's worth remembering about the cascade when it comes to CSS. So media queries *should* live at the bottom of your CSS file. If you set the width of you `body` tag to suit a mobile screen and then set it again later in the `css` file to suit a desktop sized screen, then the latest declaration will be what gets applied. So depending on whether your coming from the **mobile first** or **responsive** approach dictates how you order your CSS.

I'm going for the responsive approach so my media queries will be located beneath the CSS.

My `body` selector at the moment looks like this

`body {
  ...
  max-width: 30rem;
  ...
}`

So now I want to add the Media Query below it to adjust the `max-width` of my selector when it gets less than `30em`

`body {
  ...
  max-width: 30rem;
  ...
}
@media (width <= 30em) {
  body {
    max-width: 90%;
    }
  }`

This now allows our content to remain the same but the containers dimensions of the content blocks change and adapt according to the screen size.

I've gone for a 90% width here to give the content a bit of breathing room from the edge of the screen.

## Conclusion

I'll continue adding in some other media queries as I go but this will be the template I use.

The sites slowly coming together and I'm loving the creative process, the code and the _feels_ I get when creating something for other people to use.

Why did I stop?

Next up, I want to add some dates to these posts so I can keep up to date.
