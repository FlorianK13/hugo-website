---
date: '2024-11-20'
draft: true
title: 'Get the Mastodon Author tag for your Hugo-powered Blog'
---
With their recent blog post *[Highlighting journalism on Mastodon](https://blog.joinmastodon.org/2024/07/highlighting-journalism-on-mastodon/)*, the creators of Mastodon announced something that is really awesome. From version 4.3.0 onwards, authors of blog posts and articles can be directly visible below shared links on Mastodon. If you write something interesting and someone shares this link on the fediverse, people see your profile - your profile is linked to the article. This is a great feature for writers to boost their profiles in the fediverse.

It is also a feature you would not find on any of the other, capital-driven, social media sites. It's a feature that enhances the posting of links, directing users to your blog or media website. Users leaving the website is a core fear of any company that runs on selling your attention by bombarding you with ads. But Mastodon is different. Mastodon is [financed by its users](https://opencollective.com/mastodon). Mastodon lives the open web. **Mastodon is not afraid of links.**

## You have a Hugo powered Blog and want the Mastodon creator tag as well? Here's what you need to do!
To appear as author below links in mastodon, you need to do two things: You need to have a `meta` tag in the head of your articles, and you need to verify your website domain in your mastodon account.

To get the `meta` tag on your Hugo powered blog, follow these steps:
1. Most of you will use Hugo together with some theme - I use the PaperMod theme for example. You first need to navigate to the `themes/<YourTheme>/partials/head.html` file and copy its content. You then create a new file in `layouts/partials/head.html` and paste the content in there. By doing so, you tell hugo to use your newly provided `head.html` template instead the one provided by the theme. However nothing will change on your site, since both files are identical.
1. In the newly created `head.html`, search for the place where all the other `<meta>` are placed. Add this code:
    ```html
    {{ with .Site.Params.fediverse_creator }}
    <meta name="fediverse:creator" content="{{ . }}" />
    {{ end }}
    ```
1. Go to your config file in the root of your repository, a file usually called `hugo.yml`, `conig.yml`, `hugo.toml` or so. Add the parameter `fediverse_creator`:
    ```yml
    params:
        fediverse_creator: "@your-name@your-mastodon-server" 
    ```

Next, you need to allow your profile to be connected to links from your website. To do so, open the Edit Profile page in your mastodon account, navigate to the Verification tab, and add your website domain.

You will now have the author tag appearing below your links. If you move to another mastodon server, just change the `fediverse_creator` parameter in your config file.