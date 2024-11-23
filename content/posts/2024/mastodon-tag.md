---
date: '2024-11-20'
draft: false
title: 'Make Your Hugo Blog Posts Shine on Mastodon'
cover:
  image: img/posts/202411-mastodontag.jpg
---
With their recent blog post *[Highlighting journalism on Mastodon](https://blog.joinmastodon.org/2024/07/highlighting-journalism-on-mastodon/)*, the creators of Mastodon announced incredibly awesome. From version 4.3.0 onwards, authors of blog posts and articles can be directly visible below shared links on Mastodon. If you write something interesting and someone shares this link on the fediverse, people will see your profile linked to the article. This is a great feature for writers to boost their profiles in the fediverse.

It is also a feature you won't find on any other capital-driven social media platform. It's a feature that enhances the posting of links, directing users to your blog or media website. On ad-based platforms, users leaving the website is a core fear for companies whose profit comes from your attention and that are bombarding you with ads. But Mastodon is different. Mastodon is [financed by its users](https://opencollective.com/mastodon). Mastodon lives in the spirit of the open web. **Mastodon is not afraid of links.**

## You have a Hugo powered Blog and want the Mastodon creator tag as well? Here's what you need to do!
To appear as author below links in mastodon, you need to do two things: You need to have a `meta` tag in the head of your articles, and you need to verify your website domain in your mastodon account.

To get the `meta` tag on your Hugo powered blog, follow these steps:
1. Most of you will use Hugo together with a theme (e.g., PaperMod). First, navigate to the `themes/<YourTheme>/partials/head.html` file and copy its content. 
1. Next, create a new file in `layouts/partials/head.html` and paste the content there. By doing so, you instruct Hugo to use your newly created `head.html` template instead of the one provided by the theme. For now, nothing will change on your site since both files are identical.
1. In the newly created `head.html`, locate the section where all other `<meta>` tags are placed and add the following:
    ```html
    {{ with .Site.Params.fediverse_creator }}
    <meta name="fediverse:creator" content="{{ . }}" />
    {{ end }}
    ```
1. Locate your config file in the root of your repository. The config file is usually named `hugo.yml`, `conig.yml`, `hugo.toml` or similar. Add the parameter `fediverse_creator`:
    ```yml
    params:
        fediverse_creator: "@your-name@your-mastodon-server" 
    ```

Next, you need to allow your Mastodon profile to be connected to links from your website. To do so, open the `Edit Profile` page in your mastodon account, navigate to the Verification tab, and add your website domain.

You will now have the author tag appearing below your links. If you move to another mastodon server, just change the `fediverse_creator` parameter in your config file.

## Edits
As [@tinsukE](https://mas.to/@tinsuke) pointed out, for many templates including PaperMod it is not necessary to copy the whole `head.html` file. Instead you can insert the `<meta>` tag within an `extend_head.html` file, as shown [here](https://github.com/adityatelange/hugo-PaperMod/blob/master/layouts/partials/extend_head.html). This brings the advantage that future updates that the theme introduces to the `head.html` file will still be integrated in your website.