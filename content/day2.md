---
layout: _main.njk
title: Getting started with 11ty
---

# Day 2 setting up and tweaks

Yesterday, I got the the barebones working on 11ty which is a good step forward given my total procrastination and I guess, *fear* of starting anything new because I've been that long out of the game, it's all a bit *foggy*.

My first task this evening is to get some includes working. We set up the `_includes` folder yesterday and added that config to our `.eleventy.js` file so 11ty knows where to look when we want to include a *partial* or other chunk of repeatable code.

## includes

I guess the easiest chunk to start with is our `<footer>`. This will be the same across all of our pages so I created a new file in my `_includes` folder called `_foot.html`.

This file can include anything, as long as it can be parsed. You can't fill the file with `php` and expect 11ty to work it all out and parse it correctly, but it will take `html` and the like.


So the footer is fairly basic. All it needs (if at all), is a copyright or string of text or whatever. Its more to signify the end of the page.  My `_foot.html` looks like this.

`<footer>CroydonCreativ.es 2011-2020</footer>`

Simple and straight forward.

Now I've jumped back into my `_main.njk` template I built yesterday and I want to insert this footer at the end of the page. It'd normally nestle in just before the closing `</body>` tag.

Here, instead of putting our footer tags & end text, we'll include the `nunjucks` method of including our `_foot.html` partial

{% raw %}{% include "_includes/_foot.html" %}{% endraw %}

Which will now insert our footer into each page which uses our `_main.njk` template.

I've done the same with my header so that is stored in it's own separate file too; just in case I want the same header across all pages but different layouts.

## Fonts

The main typeface used by CroydonCreativ.es is **Adelle Bold**. Adobe Fonts (formely TypeKit) serves this up as a webfont and gives me a css link to include in the head of my page.

I'd quite like all headings in Adelle. It's too much for body text though.

So my heading selector within my CSS will read like so:
`h1, h2, h3, h4, h5, h6 {
  font-family: "adelle";
  font-weight: 700;
}`

## CSS

Speaking of CSS, I've created a an `assets/css` and `assets/images` folder within my `_site` folder. I can store all of my css & images in their respective folders to keep things clean.

Now when I last used CSS in anger, I was making the switch from `LESS` to `Sass`. I used to be a big `LESS` advocate; I even produced [a video course]("https://www.packtpub.com/product/learning-less-video/9781783989867") with [Packt]("https://packtpub.com"). But `Sass` seemed to be advancing faster, and building in more features.

For the moment, I'll be using clean CSS whilst I try to catch up with more modern processes.

I've created a little colour palette, some header images, and roughly set my typefaces.

## Fin

Quick day today. I've started a little list of things I want to roll in to the CroydonCreativ.es page.

* Responsive design that adapts to devices; it should be fairly easy with this site.
* an email sign up *just in case* a 10yr anniversary thing does happens
* responsive images for higher resolution screens
* A CSS Reset. I previously used Meyers CSS reset but I'm sure there's better methods now.
* New Layout & CSS functions?
* night & day modes.
