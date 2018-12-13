[![MIT license](https://img.shields.io/badge/License-MIT-blue.svg?style=flat)](https://github.com/htr3n/hyde-hyde/blob/master/LICENSE.md) ![GitHub release](https://img.shields.io/github/release/htr3n/hyde-hyde.svg) ![GitHub stars](https://img.shields.io/github/stars/htr3n/hyde-hyde.svg) ![GitHub forks](https://img.shields.io/github/forks/htr3n/hyde-hyde.svg) ![GitHub issues](https://img.shields.io/github/issues/htr3n/hyde-hyde.svg) ![GitHub issues closed](https://img.shields.io/github/issues-closed/htr3n/hyde-hyde.svg)

# Hyde-hyde

__`Hyde-hyde`__ is a [Hugo](https://gohugo.io)'s theme inspired and derived from @spf13's [Hyde](https://github.com/spf13/hyde.git) and [Nate Finch's blog](https://npf.io). 

## Breaking Changes

Since version 2.0, __`hyde-hyde`__ has been overhauled and, therefore, might cause some disruptions.

* The main styles are refactored and redeveloped using SCSS (see [_static-src/scss_](https://github.com/htr3n/hyde-hyde/blob/master/static-src/scss)),  `poole.css` and `hyde.css` are no longer needed because `hyde-hyde.scss` already incorporates relevant elements (I still keep them there for reference purpose)
  * Per PR [#45 by [@jd4no](https://github.com/jd4no), `hyde-hyde` can use SCSSs diectly in the templates instead of the generated CSSs. The generated CSSs and the generated resources are still kept in `hyde-hyde` in order to ensure the demo on [Hugo theme site](https://themes.gohugo.io) working.
* The layouts have been heavily restructured and modularised further (see [_layouts_](https://github.com/htr3n/hyde-hyde/blob/master/layouts))
* Adding '[_Portfolio_](https://github.com/htr3n/hyde-hyde/blob/master/layouts/portfolio)' page inspired by Xiaoying Riley (@3rdwave_themes) [Developer-Theme](https://github.com/xriley/developer-theme)
* Switching to use system fonts instead of Web fonts (e.g. privacy issues)
* Experimenting a collapsible menu in mobile mode
* Adding _Table of Contents_
  * Configure using `.Site.Params.toc` with two possible value: "hugo" (using Hugo `{{ .TableOfContents }}`, and "tocbot" (using [Tocbot](https://tscanlin.github.io/tocbot/)), remove `.Site.Params.toc` to disable TOC
  * Tocbot can be configured in [_layouts/partials/page-single/footer.html_](_layouts/partials/page-single/footer.html_) with options as described in [its documentation](https://tscanlin.github.io/tocbot/#api)

For more details, please refer to [CHANGELOG](https://github.com/htr3n/hyde-hyde/blob/master/CHANGELOG.md).  A real site in action can be found [here](https://htr3n.github.io) and its [WIP source](https://github.com/htr3n/htr3n-blog) for reference.

## Usage

### Installation

__`Hyde-hyde`__ can be easily installed as many other Hugo themes:

```sh
$ cd HUGO_PROJECT

# then either clone hyde-hyde
$ git clone https://github.com/htr3n/hyde-hyde.git themes/hyde-hyde

# or just add hyde-hyde as a submodule
$ git submodule add https://github.com/htr3n/hyde-hyde.git themes/hyde-hyde
```

After that, choose `hyde-hyde` as the main theme.

* `config.toml` 

```toml
theme = "hyde-hyde"
```

* `config.yaml`

```yaml
theme : "hyde-hyde"
```

That's all. You can render your site using `hugo` and see `hyde-hyde` in action.

### Options

__`Hyde-hyde`__ essentially inherits most of Hyde's [options](https://github.com/spf13/hyde#options). There are some extra options though

* `highlightjs = true`: use [highlight.js](https://highlightjs.org) instead of Hugo built-in support for code highlighting

  * `highlightjsstyle="highlight-style"`: only when `highlightjs = true`, please choose one of many _highlight.js_'s [styles](https://highlightjs.org/static/demo).
  * Since [v2.0.1](https://github.com/htr3n/hyde-hyde/tree/v2.0.1), highlighting for each page can be fine-tuned in the front matter, for example
    * `highlight = false`  (default `true`)
    * `highlightjslanguages = ["swift", "objectivec"]` 

* `postNavigation = true|false` (default `true`): Setting to `false` will disable the navigation _Previous Post_/ _Next Post_

* `relatedPosts = false|true` (default `false`): Setting to `true` allows related posts. Please refer [here](https://gohugo.io/content-management/related) for more details on related contents with Hugo.

* `GraphCommentId = "your-graphcomment-id"`: to use [GraphComment](https://graphcomment.com) instead of the built-in [Disqus](https://disqus.com). This option should be used exclusively with `disqusShortname = "disqus-shortname"`.

* `UtterancesRepo = "your-repo-name"`: to use [Utterances](https://utteranc.es/) instead of the built-in [Disqus](https://disqus.com). This option should be used exclusively with `disqusShortname = "disqus-shortname"`.
  * `UtterancesIssueTerm = "pathname"` Method for Utterances to match issue's to posts (pathname, url, title, og:title)
  * `UtterancesTheme = "github-light"` Theme for Utterances (github-light, github-dark)

* `[params.staticman]`: to use [Staticman](https://staticman.net/) for static comments.

  ```toml
  [params.staticman]
      api = "https://staticman3.herokuapp.com/v3/entry/{gitlab|github}/{username}/{repo}/{branch}/comments"
  [params.staticman.recaptcha]
      sitekey = # your own reCAPTCHA site key
      secret = # encrypt reCAPTCHA site secret with https://staticman3.herokuapp.com/v3/encrypt/{secret}
  ```

* `[params.social]`: in this section, you can set many social identities such as Twitter, Facebook, Github, Bitbucket, Gitlab, Instagram, LinkedIn, StackOverflow, Medium, Xing, Keybase.

  ```toml
  [params.social]
  	twitter = "htr3n"
  	keybase = "htr3n"
  	github = "htr3n"
  	...
  ```

  * Per PR [#56](https://github.com/htr3n/hyde-hyde/commit/5ed13e17400bbc09a342b60fd50cd9fe3e6f1525), Gravatar pics can be used exclusively to `.Site.Params.authorimage` via the parameter `.Site.Params.social.gravatar`

    * ```toml
      [params.social]
      	gravatar = "your.email@domain.com"
      ```

### Customisations

* Most of the customisable SCSS styles in [_static-src/scss/hyde-hyde_](https://github.com/htr3n/hyde-hyde/blob/master/static-src/scss/hyde-hyde) and Hugo templates in [_hyde-hyde/layouts_](https://github.com/htr3n/hyde-hyde/blob/master/layouts) are modularised and can be altered/adapted easily.

## Portfolio

Since version 2.0+, I added a portfolio page just in case. If you need it, simply add a menu section '_Portfolio_' in `config.toml` as following.

```toml
[[menu.main]]
    name = "Portfolio"
    identifier = "portfolio"
    weight = xyz
    url = "/portfolio/"
```

In the folder `content` , create a subfolder `portfolio` and use the following folder/content structure as reference.

```
$ tree portfolio
portfolio
├── _index.md
├── p1.md
├── p1.png
├── p2.md
├── p2.png
    ...
├── pn.md
└── pn.png
```

As I design the section _portfolio_ to be rendered as _list_,  `_index.md` can be used to set the title for your portfolio (you can read more about `_index.md` [here](https://gohugo.io/content-management/organization/#index-pages-index-md)). For instance, when I want to set the title of my portfolio "_Projects_", the front matter of `_index.md` will be:

```markdown
---
title: 'Projects'
---
```
The remaining of `_index.md` will be ignored.

For each project, just create a Markdown file with the following parameters in the front matter:

```markdown
---
title: "Project P1's Title"
description: "A short description"
date: '2018-01-02'
link: 'https://project-p1.com'
screenshot: 'p1.png'
layout: 'portfolio'
featured: true
---
Here is a longer summary of the project. You can write as long as you wish.
```

> __Note__:
>
> * `date` is important to sort the project chronologically
> * `layout 'portfolio'` is important as you don't want your project's page appear in the list of posts in the main page of your Web site but only in the _Portfolio_ ;)
> * `featured: true` : when you want to show a project as featured project. It is default to `false`. Note that only one project should be marked `featured: true` , otherwise, the result could be random as [the Hugo template](https://github.com/htr3n/hyde-hyde/blob/master/layouts/partials/portfolio/content.html) will take the first one.
> * The body of the Markdown file will be the summary of the project.

If you want to adjust the portfolio page to your needs, please have a look at the [main template](https://github.com/htr3n/hyde-hyde/blob/master/layouts/portfolio/list.html), that uses this [partial template](https://github.com/htr3n/hyde-hyde/blob/master/layouts/partials/portfolio/content.html) and [this SCSS style](https://github.com/htr3n/hyde-hyde/blob/master/static-src/scss/hyde-hyde/_project.scss).

## Some Screenshots

### Main page

![hyde-hyde main screen](https://github.com/htr3n/hyde-hyde/raw/master/images/main.png)

### A post

![A post in hyde-hyde](https://github.com/htr3n/hyde-hyde/raw/master/images/post.png)

### Portfolio

![Portfolio hyde-hyde](https://github.com/htr3n/hyde-hyde/raw/master/images/portfolio.png)



### Mobile Mode with Collapsible Menu

<img src='https://github.com/htr3n/hyde-hyde/raw/master/images/mobile.png' alt='hyde-hyde in mobile mode' width='60%'>

## Author(s)

* Original developed by [Mark Otto](https://github.com/mdo)

* Hugo's `hyde` ported by [Steve Francia](https://github.com/spf13)

## License

Open sourced under the [MIT license](LICENSE.md)
