# al-folio

[![build status](https://travis-ci.org/alshedivat/al-folio.svg?branch=master)](https://travis-ci.org/alshedivat/al-folio)
[![demo](https://img.shields.io/badge/theme-demo-brightgreen.svg)](https://alshedivat.github.io/al-folio/)
[![gitter](https://badges.gitter.im/alshedivat/al-folio.svg)](https://gitter.im/alshedivat/al-folio?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)
![GitHub](https://img.shields.io/github/license/alshedivat/al-folio?color=blue)
[![GitHub stars](https://img.shields.io/github/stars/alshedivat/al-folio)](https://github.com/alshedivat/al-folio)
[![GitHub forks](https://img.shields.io/github/forks/alshedivat/al-folio)](https://github.com/alshedivat/al-folio/fork)

A simple, clean, and responsive [Jekyll](https://jekyllrb.com/) theme for academics.
If you like the theme, star the [original repo](https://github.com/alshedivat/al-folio)! If you'd like to make a similar site for yourself, feel free to fork this repo or the original. I provide some links [below](#below) that helped me tweak some technical things in my branch.


## Getting started

For more about how to use Jekyll, check out [this tutorial](https://www.taniarascia.com/make-a-static-website-with-jekyll/).
Why Jekyll? Read this [blog post](https://karpathy.github.io/2014/07/01/switching-to-jekyll/)!


### Installation

You will need to have [Ruby](https://www.ruby-lang.org/en/downloads/) and [Bundler](https://bundler.io/) installed on your system (*hint: for ease of managing ruby gems, consider using [rbenv](https://github.com/rbenv/rbenv)*), first [fork](https://guides.github.com/activities/forking/) the theme from `github.com:alshedivat/al-folio` to `github.com:<your-username>/<your-repo-name>` and do the following:

```bash
$ git clone git@github.com:<your-username>/<your-repo-name>.git
$ cd <your-repo-name>
$ bundle install
$ bundle exec jekyll serve
```

This runs a local server that you can use to play around with the site. Changes will update almost instantly. But if you change anything in the `_config` file, you will need to restart the server to observe the changes.
**Commit** your changes as you go.
Once you feel like your site is ready to go, deploy it to [GitHub Pages](https://pages.github.com/) by running the deploy script:

```bash
$ bin/deploy --user
```
By default, the script uses the `master` branch for the source code and deploys the webpage to `gh-pages`.
The optional flag `--user` tells it to deploy to `master` and use `source` for the source code instead. Using `master` for deployment is a convention for [user and organization pages](https://help.github.com/articles/user-organization-and-project-pages/). **Pay attention to which branch you are working on**. I cannot stress this enough. I nearly lost my mind running the above script when I was working on `master`, and ended up watching my changes evaporate before my eyes. I recommend just working on the `source` branch locally and then running the script as above (just please please please check which branch you're committing to!).

**Note:** when deploying your user or organization page, first make sure the `_config.yml` has `url` and `baseurl` fields as follows.

```
url:  # should be empty
baseurl:  # should be empty
```

<a id="below"></a>
## Things tweaked on mariakhoudary.com

1. I spent a ton of time troubleshooting how to host my default mode archive (did you know soundcloud limits your uploads to 3 hours on the free version?? I didn't!). [This post](https://portalzine.de/dev/html5/hosting-mp3-files-on-google-drive-html5-audio-player/) sealed the deal.
2. I followed [this advice](https://gitter.im/alshedivat/al-folio?at=5f5a8890b190f2328e656862) for getting my CV to be a link on the header and not its own page.
3. I hard-coded the order of my sites by creating a variable in the YAML header called `order`. Then in `_includes/header.html`, I went to the section `Other pages` and changed the first line after that comment to `{% assign sorted_pages = site.pages | sort: "order" %}`.
4. Something I'm still trying to figure out how to do: insert a hyperlink under my photo on the `about` page. --> figured it out! you need to use html formatting because it's a variable. template in case, like me, you're learning html as you build your site: `Wondering how to <a href="https://namedrop.io/mariakhoudary" target="_blank">pronounce my name</a>?`
5. I'm using [this site](https://www.readmodwrite.com/2019-01-18-jekyll-seo-tags/) to increase my SEO. Will report experience with each method.
    - [jekyll-sitemap](https://github.com/jekyll/jekyll-sitemap)


## FAQ

Here are some frequently asked questions.
If you have a different question, please ask on [gitter](https://gitter.im/alshedivat/al-folio).

1. **Q:** When I preview my website locally everything looks great, but when I deploy it on GitHub bibliography Liquid tags are not recognized.
   How do I fix this? <br>
   **A:** GitHub Pages rendering does not support certain Jekyll plugins, and `jekyll-scholar` that we use to render bibliography is one of them. Please make sure you deploy your website to GitHub using `bin/deploy` script that circumvents the issue.

2. **Q:** When I deploy my fork of al-folio, it says `Deployed successfully!`
   But when I open `<my-github-username>.github.io`, I get `Page not found (404)` error.
   How do I fix this? <br>
   **A:** For personal webpages, please run `bin/deploy --user`.
   (See also relevant past issues: [#5](https://github.com/alshedivat/al-folio/issues/5), [#49](https://github.com/alshedivat/al-folio/issues/49), [#86](https://github.com/alshedivat/al-folio/issues/86).)


## License

The theme is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).

Originally, **al-folio** was based on the [\*folio theme](https://github.com/bogoli/-folio) (published by [Lia Bogoev](http://liabogoev.com) and under the MIT license).
Since then, it got a full re-write of the styles and many additional cool features.
