# Mautic - Grav Plugin

This is [Grav CMS](http://getgrav.org) plugin that helps you configure [Mautic](https://mautic.org) tracking and converts markdown "links" into Mautic Form Embed code.

# Installation

Installing the Mautic - Grav plugin can be done in one of two ways.

## GPM Installation (Preferred)

The simplest way to install this plugin is via the [Grav Package Manager (GPM)](http://learn.getgrav.org/advanced/grav-gpm) through your system's Terminal (also called the command line).  From the root of your Grav install type:

    bin/gpm install mautic

This will install the Mautic - Grav plugin into your `/user/plugins` directory within Grav. Its files can be found under `/your/site/grav/user/plugins/mautic`.

## Manual Installation

To install this plugin, just [download](https://github.com/mautic/mautic-grav/archive/master.zip) the zip version of this repository and unzip it under `/your/site/grav/user/plugins`. Then, rename the folder to `mautic`.

You should now have all the plugin files under

    /your/site/grav/user/plugins/mautic

# Config Defaults

```
enabled: true
url: true
```

If you need to change any value, then the best process is to copy the [mautic.yaml](mautic.yaml) file into your `users/config/plugins/` folder (create it if it doesn't exist), and then modify there.  This will override the default settings.

# Usage

## Mautic tracking

Tracking image works right after you enable the plugin, insert the Base URL and save the plugin. That means it will insert 1 px gif image loaded from your Mautic instance. You can check HTML source code (CTRL + U) of your Grav website to make sure the plugin works. You should be able to find something like this:

```
<script>
    var img = new Image();
    img.src = 'http://yourmautic.com/mtracking.gif?d=...';
    img.alt = 'mautic is open source marketing automation';
</script>
```

There will be probably longer URL query string at the end of the tracking image URL. It is encoded additional data about the page (title, url, referrer).

## Mautic Form Embed

To use this plugin you simply need to include a Mautic Form ID in markdown link such as:

```
[plugin:mautic](FORM_ID)
```

Example: `[plugin:mautic](8)` will load Mautic form with ID = 8.

This code snippet will be converted into the following:

```
<script type="text/javascript" src="http://yourmautic.com/form/generate.js?id=8"></script>
```
