---
layout: _main.njk
title: Getting started with 11ty
---

# Starting 11ty
11ty seems to be the talk of the town at the moment. A lightening fast static site generator that’s doing the rounds and everyones giving it a whirl… including me!

I was chatting with the [On The Side](link) community earlier this week when conversation got onto the CroydonCreativ.es, a local community we started nearly 10 years ago but fizzled out back in 2016.

For nostalgic value, I hit up the website to remind myself of some of the content, only to be greeted with a 404.

Had I let the domain lapse? No. That still appeared active so after a little further digging, I had moved the folder and not redirected the domain. Old school error.

So because I’ve been meaning to update the CC website *for the last 5 years*, I thought I’d use it as an opportunity to give 11ty a go! After all, the CC site should now be a simple static holding page.

## Step 1, the install.
So it would appear my mac is still running Node v6. Current version is 12 so a little out of date.

After updating node, I followed the instructions on the [11ty]() website to install it locally

@$ npm install --save-dev @11ty/eleventy@

Now we’re cooking with gas.

## Step 2, general site setup
First things first, I created a `package.json` file. I’m not too sure why, but the guide I was following suggested it.

Next, on my local dev area, I’ve created a @content@ folder, @layouts@ folder and `_includes` folder. I like to keep things organised. The names should be fairly self explanatory but @content@ is where my `md` files live. This creates my content. The `_layouts` folder keeps track of all my layouts; I may have different layouts for different pages and `_includes` is where all my partial code chunks are kept. My headers & footers that get re-used throughout the site.

The CC site is fairly straight forward so the above is probably overkill but it’s good to get into the habit of keeping folders organised. In reality, the CC site will only have one page, maybe two. It’ll use the same layout and includes will be minimal.

For configuration, i created a `.eleventy.js` file.

And then I `git init` the root folder, create a `.gitignore` and commit everything to git for version control because I don’t do that enough at all!

## Step 3 Configuration

the `.eleventy.js` file is where the configuration is kept for our site and it uses `JS` to determine what happens and where.

For the moment, we’ll just use it to tell 11ty where our includes, layouts & content are stored. My `.eleventy.js` file looks like this: -

`module.exports = {
    dir: {
        includes: “../_includes",
        layouts: “../_layouts",
        input: "content"
    }
};`

Here, we’re telling 11ty where our includes and layouts reside, **relative to where our content lives** hence the `../` at the beginning of each folder name.

@content@ is fairly self explanatory but we’ve created it’s own folder to keep the content separate from the templating & layout side of things.

*It’s worth noting that it’s good behaviour to add underscores to the beginning of your includes & layouts folders & files within.*

## Step 4 Layouts
Layouts are for setting out your page. It’ll generally be a HTML document with the doctype, head, body & html tags but instead of actual content, we use our templating system tags. I’ve been using Nunjucks because I like the name.

For Nunjucks, we use @{{ title }}@ in place of where the title will appear, such as in between the `<title>` tags and `{{ content | safe }}` for where we want the content to appear. The `safe` portion of this tag tells 11ty that this content need not be automatically escaped.

So our initial layout is called `_main.njk` and looks something like this: -

`<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title>{{ title }}</title>
  </head>
  <body>

    {{ content | safe }}

  </body>
</html>`

## Step 5 Content
Next up is content. We want to fill those Nunjucks tags with content right?

In the content folder, I’ve created a markdown file called `index.md` which will be treated as my index or homepage. I could create an `about.md` file which will tell 11ty to build this as `croydoncreativ.es/about` which is neat!

So at the top of the markdown file, we use something 11ty terms as `front matter`; this is effectively a config portion for your content and it looks a little like this:

`---
layout: _main.njk
title: CroydonCreativ.es
---`

The @layout@ tag tells 11ty which layout to use, in this instance, it’s 'main.njk' and the 'title' tag is the title of the document. This replaces the '{{ title }}' tag we include as part of the layout.

After this 'front matter', we continue to write our content in Markdown.

## Fin
This is the story so far. Next step is to get some includes working so that we can build out a header & footer. And then it’s adding some design flair in.

That’s the fun bit :)
