---
layout: post
title:  "Awesomeness of Sublime Text Editor"
date:   2014-12-06 16:57:00
categories: Sublime
---

[Sublime Text](http://www.sublimetext.com/) is one of the coolest text editor for code I have come across. If you are new to Sublime and are really interested in learning about the power of Sublime I would highly recommend you to attend free video course on [Tuts+ conducted by Jeffrey Way] (https://code.tutsplus.com/courses/perfect-workflow-in-sublime-text-2).

If you are in a hurry and would like to quickly know some benefits of Sublime Text continue reading.

## Shortcut keys

In the shortcut keys I'll be mentioning `super` which is `cmd` key if you are using **Mac** and `ctrl` key if you are using **Window**.

* `super + p` - Open any file using fuzzy search
* `super + shift + p` - Access to complete Sublime menu using fuzzy search
* `super + r` - Search methods in current file
* `super + i` - Instant incremental search in current file
* `super + /` - Toggle commenting out line
* `option   ` - For column select using mouse
* `super + w` - Closes current tab
* `super + =` - Zoom in
* `super + _` - Zoom out
* `super + d` - Selects next matching word
* `super + ctrl + g` - Select all matching words
* `super + shift + l` - Writes on all selected lines at the same time

## Package Control

Heart of Sublime Text are its plugins and the easiest way to install plugins is through Package Control.

Install Package control easily using steps mentioned over here <a href="https://sublime.wbond.net/installation">https://sublime.wbond.net/installation</a>

Once Package control is installed just press `super+shift+p` to open command prompt and type *install* and press enter to open search for package control. 

Search for any package you want to install and just press enter. Some plugins may require you to restart Sublime.

## Snippets

Snippets are smart templates that will insert text for you and adapt it to their context. For e.g. in an html file if you type in `<a` and then press tab it will complete the tag template for you `<a href=""></a>`.

To see what snippets are already installed with Sublime, press `super+shit+p` and type **Snippets**, select the one you want to use and press enter.

You can also install snippets created by community. For e.g. I use groovy language and by default Sublime doesn't come with groovy snippets. To install them open command prompt using `super+shit+p` and type **install**, press enter to open Package control and type **groovy snippets**, select the groovy snippets plugin and press enter.

To test groovy snippets create a new groovy file and type `for` and press `tab` **for** syntax will be completed by groovy snippets.

You can even create you own [snippets](http://sublime-text-unofficial-documentation.readthedocs.org/en/latest/extensibility/snippets.html#snippets-file-format).

## Plugins

As mentioned above plugins is what makes Sublime Text so special, and now that we have already installed package control, lets review some nice plugins.

All plugins mentioned below can be installed using Package Control. Press `super+shift+p` type **install** press enter to open Package control search, type in the name of plugin you want to install and press enter.

#### [Emmet](http://emmet.io/)
Emmet (previously known as Zen Coding) is a web-developer’s toolkit that can greatly improve your HTML & CSS workflow.

#### [Advanced New File](https://sublime.wbond.net/packages/AdvancedNewFile) 
This plugin allows for faster file creation within a project. Press `supet+alt+n` and type in complete path of the file with extension you want to create and press enter. It will also create directory if it doesn't already exist

#### [Sublime Linter](http://www.sublimelinter.com/en/latest/)
SublimeLinter is a plugin for Sublime Text 3 that provides a framework for linting code. Whatever language you code in, SublimeLinter can help you write cleaner, better, more bug-free code.

#### [Gist](https://github.com/condemil/Gist)
A Sublime Text 2/3 plugin for creating and editing GitHub Gists.

#### [Http Requester](https://github.com/braindamageinc/SublimeHttpRequester)
Makes HTTP requests using the selected text as URL + headers. Useful for testing REST APIs from Sublime Text 2 editor.

#### [Live Reload](https://sublime.wbond.net/packages/LiveReload)
A web browser page reloading plugin for the Sublime Text editor.

## Conclusion

I have hardly covered 10% of what Sublime Text can do. Again do attend the free video course on [Tuts+ conducted by Jeffrey Way] (https://code.tutsplus.com/courses/perfect-workflow-in-sublime-text-2).

Thanks and I hope it was helpful.


