---
date: '2026-01-09'
draft: false
title: 'Moving from github pages to codeberg pages'
---

There are two code platforms I'm active on. One is run by a multi‑billion‑dollar cooperation, one is run by a small association belonging to its members, including me. Sadly I am way more active on the multi‑billion‑dollar cooperation platform. I want to change that. So with the [Digital Indepenence Days](https://di.day) I wanted to move something to the nice, community driven platform. 

Here's how I moved one project from **[github pages](https://docs.github.com/en/pages) to [codeberg pages](https://codeberg.page/)**.

## What are the differences

Overall, github pages and codeberg pages offer the same functionality. They host static websites from your git repository. Both can be accessible through their domain (*USERNAME.github.io/REPOSITORY vs USERNAME.codeberg.page/REPOSITORY*) or through a domain that you provide. Both integrate TLS (you can access the site via https). Both are free of charge. The differences are only minor:

* codeberg.page is in maintenance mode and does not integrate new features right now
* codeberg.page might be less stable, since they cannot throw infinite money on their hardware problems

## How to use codeberg pages

1. Create a repository on codeberg.
2. Add your html files directly to the repo, or choose some static site generator.
3. Make sure that your final html/js/css files are on a branch called `pages`.
4. *Optional*: If you want to use a custom domain, insert a `.domains` file as described on [codberg.page](https://codeberg.page). Modify your DNS entry to point to the codeberg servers.

## Final remarks
As a coding community, we are strongly dependant on github. If Microsoft, the owner of github, starts to do stupid things, we are really fucked up. Let's start to build up some alternatives - or at least support the people that build the alternative for us.

You can [join the codeberg association](https://join.codeberg.org/) and support them with your annual membership fees. Who knows, we might need their platform earlier then we expect.