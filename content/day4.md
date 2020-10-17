---
layout: _main.njk
title: Day 4 - Losing track of days
date: 2020-10-17
update: Mon, 19 Oct 2020
---

I'm thoroughly enjoying the build of the **CroydonCreativ.es** site using 11ty. It's great to get back into the swing of code and design. A gentle creative outlet and hobby.

We're obviously on day 4 now and we've covered some fun stuff so far and I'm aware of also got some additional features and function that I want to roll in so there's going to be a fair amount of articles to come.

I realise 11ty isn't a blogging system in the normal sense but it can be a blog. I wanted to roll some dates and date tracking into each piece of content to not only have a 'posted' date but also a 'modified' date to.

I'm not beating around the bush here. I've not coded in anger or done any serious front-end code for a good while now and what I remember _may not_ be the right way to do things _now_.

## A note

I realise the proper way to do this would be to learn and research the current modern ways of doing *anything* in front end development and *then* writing about it but I find that a trigger for my procrastination and probably why I've shyed away from front-end for a number of years now. Not knowing *modern techniques* has been a barrier for me.

**So** the idea is to code how I used to do things and write about it and then *modify* the articles when I've learnt how to better prepare and write the code.

Take yesterdays `media query` post. This was primarily based on my `media query` knowledge from 6 years ago. I noticed that `media queries level 4` is now the standard, and that brings an array of new features with it. What I wrote about yesterday may not be the best & most modern way to code media queries and I will update or *modify* the post when I'm learnt new tricks!

## Show me the date.

First, let's set the *Posted date*. The 11ty docs have a great primer on [content dates]("https://www.11ty.dev/docs/dates/") and it all seems fairly straight forward. It's a two part process. The first being where we add the date to our markdown files and the second part, displaying that in our templates.

### Part 1 - Set the date

I mentioned the `front matter` on 11ty templates a few days ago. Here is where we add our dates.

This is entered in yyyy-mm-dd format so today's date will be entered as

`---
date: 2020-10-17
---`

### Part 2 - Show the dates

Now that we've got the date set in our content, let's display that within our template.

I'll jump into my `_main.njk` file and use the `{{ page.date }}` tag to display my date.

`Sat Oct 17 2020 01:00:00 GMT+0100 (British Summer Time)`

But this gives me far too much information. I don't want to know times or even time zones so we'll take the nunjucks tag and append it with a `JS` method `toUTCSring()` so that our tag will now look like `{{ page.date.toUTCSring() }}`

`Sat, 17 Oct 2020 00:00:00 GMT`

This gives us a neater time display but still keeps the time which we don't want.

If we change that `JS` method to `.toDateString()`, it reduces the output again

`Sat Oct 17 2020`

It could still do with a little formatting though but I think that requires some additional JS tomfoolery which I'll save for another day.

So my `_main.njk` file now has this for dates:

`<div class="post__date--created">`
  `Posted: <span>{{ page.date.toDateString() }}</span>`
`</div>`

I've wrapped the date section in a div so I can style it and then wrapped the nunjucks tag in a span so I can style differently if I wanted to later.

## - Now for the modified bit.

I had hoped that 11ty would be able to pick up the `last modified` date from the markdown file and use that as the modified date during the build process but that's not been coded yet. Hope it comes soon!

So a workaround is to add an `update` field to the `front matter` portion of each piece of content *when* it gets updated and manually enter the date it's been updated. It's not ideal but it works.

`---` \n
`date: 2020-10-17`\n
`update: Mon, 19 Oct 2020`\n
`---`

and then to display this on our page, within our `_main.njk` template file, we can add `{{ update }}` and it'll reflect the date we've added in our `front matter`.

We can then use nunjucks logical templating tags to display this date *if* `{{ update }}` exists

`{% if update %}
    Updated: {{ update }}
{% endif %}`

## Conclusion

Again, it'd be sweet if this was all automatic but it's not. And really, I could just add a little 'update' paragraph at the top of any piece of content I edit but it just makes things feel a little cleaner if all the meta data is kept in one place like the `front matter`.
