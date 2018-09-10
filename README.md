# Hamburg
(based on the [vienna-theme](https://github.com/keichi/vienna) from [keichi](https://github.com/keichi))

# Overview

Hamburg is a simple and clean blog theme for [Hugo](http://gohugo.io/).
Notable features I would tell somebody are:

- Clean and flat design
- Tags
- Menu
- Support for multiple authors
- Multilingual (in every way! Author information, menus, pages, posts, tags)
- Responsive design (mobile friendly)
- Font Awesome icons
- Analytics with Google Analytics, Mixpanel or custom tracking page
- Easy to customize

# Installation

In your hugo site directory, run:

```shell
$ mkdir themes
$ cd themes
$ git clone https://github.com/hauke96/hugo-theme-hamburg
```

The theme should now be in `themes/hugo-theme-hamburg/`.

# Configuration

You may specify following options in `config.toml` of your site to make use of
this theme's features (I've not tested other options so far).

```toml
baseurl = "http://your-site.com"
defaultContentLanguage = "en"
defaultContentLanguageInSubdir = "true"
title = "Your site title"
theme = "hugo-theme-hamburg"

[params]
    # Short subtitle/tagline. This is displayed in the header.
    themecolor = "#hexcolor" # Defines the tab color in Chrome for Android.
    # To load additional CSS styles
    customCSS = ['hamburg.css']
    # Show this very user-friendly and absolutely not annoying GDPR notice at the bottom of the page
    ShowGDPRNotice = true

[languages]
    [languages.en]
        languageCode = "en"
        languageName = "English"
        subtitle = "A simple subtitle"
        # Copyright notice. This is displayer in the footer.
        copyright = "&copy; some license"
        [languages.en.menu]
            [[languages.en.menu.main]]
                name = "About"
                identifier = "about"
                url = "pages/about"
    [languages.de]
        languageCode = "de"
        languageName = "Deutsch"
        subtitle = "Ein einfacher Untertitel"
        copyright = "&copy; eine Lizenz"
        [languages.de.menu]
            [[languages.de.menu.main]]
                name = "Über"
                identifier = "about"
                url = "pages/about"
```

### Additional `vienna`-theme params
There're some other params I've not used so far. They probably work, but there's no guarantee:
```toml
[params]
    # Social accounts. Link to these accounts are displayed in the header and
    # footer.
    twitter = "Your Twitter username"
    github = "Your GitHub username"
    gitlab = "Your GitLab username"
    linkedin = "Your LinkedIn username"
    googleplus = "Your Google+ user id"
    facebook = "Your Facebook username"
    reddit = "Your Reddit username"
    hackernews = "Your Hacker News username"
    stackoverflow = "Your Stackoverflow user id (number)"
    keybase = "Your keybase.io username"
    instagram = "Your Instagram username"
    # Disqus shortname
    disqus = "Your disqus shortname"
    # Google Analytics API key.
    ga_api_key = "Your Google Analytics tracking id"
    # Mixpanel API key.
    mixpanel_api_key = "Your Mixpanel API key"
```

## Params of posts (front matter)
There're some options you can set in the header of a post or page:

```toml
# The date will be at the bottom of the page at the "Posted on ..." label
date = "2018-08-13T15:38:27+02:00"
title = "Erster Eintrag"
draft = true
author = "hauke"
# The summary will be shown at the start page or other page/post lists
summary = "Dies ist nur ein Testbeitrag um die Website zu testen."
 # This will ensure that the date is not printed
noshowdate = true
```

## Multiple authors
This theme will read the information of an author based on the language code of a page.

To support multiple authors, create a `data/<lang>/authors/name.toml` file (so e.g. `data/en/authors/hauke96.toml`). This file contains the normal author information:

```toml
name = "Your name"
avatar = "/images/avatar.jpg"
contact = "mailto:mail@foobar.com"
bio = "Something about you"
```

To support multiple languages, create multiple directories in the `data` directory. So for German (`languageCode` set to `"de"`) the above example would also have a `data/de/authors/hauke96.toml` file.

## Tracking
You can use the above configuration with e.g. Google Analytics or use your own JavaScript snippet to do so.

For a custom JavaScript snippet you have to create a `layouts/partials/tracking.html` file and put the necessary code into this file. The file (is it exists) will be embedded in the header right before the `</head>` tag.

# Usage
Add this line to your config file (e.g. `config.toml`):
```toml
theme = "hugo-theme-hamburg"
```
The theme mus therefore be stores under `themes/hugo-theme-hamburg/`.

### Temporarily
Use hugo's `-t hugo-theme-hamnburg` or `--theme=hugo-theme-hamburg` option with hugo commands.
Example:

```shell
$ hugo server -t hugo-theme-hamburg -D
```
