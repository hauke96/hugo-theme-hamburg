# Hamburg

Hamburg is a simple and clean blog theme for [Hugo](http://gohugo.io/) based on the [vienna-theme](https://github.com/keichi/vienna) from [keichi](https://github.com/keichi).

# Screenshots

## Desktop
![Beautiful on desktop devices](https://github.com/hauke96/hugo-theme-hamburg/blob/dev/images/website_desktop.png)

## Mobile
![Also beautiful on mobile devices](https://github.com/hauke96/hugo-theme-hamburg/blob/dev/images/website_mobile.png)

# Overview

Notable features I would tell somebody are:

- Consistent design
	- Clean and flat design
	- Easy to customize
	- Responsive design (mobile friendly)
	- Font Awesome icons
- Navigation
	- Tags
	- Menu
- Support for multiple authors
- Multilingual (in every way! Author information, menus, pages, posts, tags)
- Analytics with any JavaScript-Snipped based service (Google Analytics, Matomo/Piwik, ...)
- Addional shortcodes

# Installation

In your hugo site directory, run:

`git clone https://github.com/hauke96/hugo-theme-hamburg.git themes/hamburg`

The theme should now be in `themes/hamburg/`.

# Configuration

You may specify following options in `config.toml` (or `config.yaml`/`config.json`) of your site to make use of this theme's features:

```toml
baseurl = "http://your-site.com"
defaultContentLanguage = "en"
defaultContentLanguageInSubdir = "true"
title = "Your site title"
theme = "hamburg"

[params]
    # Short subtitle/tagline. This is displayed in the header.
    themecolor = "#hexcolor" # Defines the tab color in Chrome for Android.
    # To load additional CSS styles
    customCSS = ['hamburg.css']
    # Show this very user-friendly and absolutely not annoying GDPR notice at the bottom of the page
    ShowGDPRNotice = true
	subtitle = "The great example site of the hugo-hamburg-theme"
	# Since 0.57.0 there's the concept of "main sections". The files for the section "posts" are in "./content/posts/".
	mainSections = ["posts"]

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
There're some other params from the [original vienna theme](https://github.com/keichi/vienna) I've not used so far. Most of them might **not work** anymore, so there's no guarantee:
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

# Usage

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

## Shortcodes
There're some simple shortcodes to make things easier.

### Link to a tag
Creates a simple link to a tag page:
```
I like {{< linkTag veggy-food "yummi vegetarian food" >}}.
```

### Include images
Includes images and opens them in a new tab when clicked:
```
{{< img "photo.png" "What a lovely picture" >}}
```

### Get URL to an image
Creates a link to the given image
```
{{< imgUrl "photo.png" "link text" >}}
```

### Embed scaled image
Scales an image to the given size and embeds it like the shortcode `img` does.
```
{{< imgUrl "photo.png" "What a lovely picture" "500x" >}}
```
(This image is scaled to 500 pixels in width, the height is determined automatically)

## Multiple authors
This theme will read the information of an author based on the language code of a page.

To support multiple authors, create a `data/<lang>/authors/name.toml` file (so e.g. `data/en/authors/hauke96.toml`). This file contains information about the author:

```toml
name = "Your name"
avatar = "/images/avatar.jpg"
contact = "mailto:mail@foobar.com"
bio = "Something about you"
```

To support multiple languages, create multiple directories in the `data` directory. So for German as second language (`languageCode` would be `de`) the above example would also have a `data/de/authors/hauke96.toml` file.

## Tracking
You can use the above configuration with e.g. Google Analytics or use your own JavaScript snippet to do so.

For a custom JavaScript snippet you have to create a `layouts/partials/tracking.html` file and put the necessary code into this file. The file (if it exists) will be embedded into the footer next to the other tracking mechanisms.

I tested this with the Matomo analytics software, which provides a JavaScript or image-based snipped that I put into the `tracking.html`.
