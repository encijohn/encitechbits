---
layout: post
title: "How To Create Your Own Documentation Website With Jekyll / Chirpy (GitHub Pages)"
date: 2025-08-04
categories: [WebDev, GitHub Pages]
tags: [jekyll, github-pages, static-site, portfolio]
image: /assets/img/header/website-chirpy.png
---

As a tech enthusiast, I think I may be too late in my career when I realized the power of documentation. 

So if you're in your tech journey as well, I would strongly encourage you to work on your writing skills as soon as possible as it will serve you well and it will be a great backbone not just for your homelab, but in life too. Also, (I think) it makes a good impression for potential employers! 

Setting up a static site for documentation shouldn’t feel like rocket science. Usually, it is recommended to start with just buying a domain from reputable sites and have them host a WordPress Blog for you, but where's the fun in that? 

If you are looking to have more control in the inner-workings of your site, it will be best for you to have the code underneath it. 

In this guide, I’ll walk you through everything I did to spin up a clean, modern blog hosted completely for FREE on GitHub with the help of GitHub Pages, Jekyll and Chirpy!

If you're someone who wants to document your projects, create a portfolio or just wants to share your knowledge online, this will be a great starting point.

## Why Jekyll and Chirpy?

[Jekyll](https://jekyllrb.com) is a static site generator that integrates directly with GitHub Pages. [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy) is a modern theme built specifically for Jekyll and GitHub Pages, with great defaults for blogging—syntax highlighting, tags, categories, TOC, search, and more.

## Initial Setup

1. **Create a GitHub Repository**  
   Head over to the [Chirpy Starter Repo](https://github.com/cotes2020/chirpy-starter) and click **Use this template**. Name the new repo something like `username.github.io/blogname` if you want it under a subpath. Having it on a subpath is helpful just in case you would want to host multiple websites!

2. **Configure GitHub Pages**  
   Go to your new repo’s settings → Pages → set the source to the `gh-pages` branch and `/ (root)` directory.

3. **Clone and Setup Locally**  (Optional)
   ```bash
   git clone https://github.com/username/blogname.git
   cd blogname
   ```

   Install dependencies:
   ```bash
   bundle install
   ```

4. **Serve Locally for Previewing**  
   ```bash
   bundle exec jekyll s
   ```
   Then open `http://localhost:4000` in your browser.

## Customizations I Made

- **Changed baseurl:** In `_config.yml`, I set:
  ```yaml
  baseurl: "/blogname"
  ```

- **Updated site title & description**:
  ```yaml
  title: "My Blog"
  description: "Notes, Labs, and Learnings"
  ```

- **Updated the post header image** by placing it in `/assets/img/header/` and referencing it in the front matter of the post:
  ```yaml
  image: /assets/img/header/Getting-Started-With-Homelab.png
  ```

## Common Build Issues (and Fixes)

### ❌ `htmlproofer` throws `'a' tag is missing a reference`

This one’s annoying—but solvable. Chirpy renders an empty `<a>` tag when no social links are provided in your `_config.yml`, which fails the `htmlproofer` check.

#### ✅ Fix:

Add at least one social or author URL in your config like so:
```yaml
social:
  name: Your Name
  links:
    - https://github.com/username
```

Alternatively, disable or tweak the HTML proofer settings in your GitHub Actions workflow—but the cleaner fix is just to provide a valid link.

## Deployment

Once everything looks good, push to GitHub and your site should be live shortly at:

```
https://username.github.io/blogname/
```

If you’re hosting under the root domain (`username.github.io`), you can leave `baseurl` empty. If under a subpath (like `/blogname`), make sure that’s reflected everywhere.

## Final Thoughts

This setup gives you full control over your blog or documentation site—with the bonus of GitHub’s robust hosting and version control. You can write posts in Markdown, preview locally, and ship updates just by committing to `main`.

It’s fast, free, and surprisingly fun. 

For more customization, you may review the code entirely and create your own tweaks! 

---

Still a work in progress, but if this helped you in any way, keep tinkering and share your work! Self-hosting is a great way to learn.