# data-science-wiki

The wiki is hosted at https://sozy.xyz/wiki

# General wiki editing

This wiki is compiled from markdown files. 

See [this](https://www.markdownguide.org/basic-syntax/) for how to write markdown.

You can also (and are recomended to) use [obsidian.md style internal links](https://help.obsidian.md/How+to/Internal+link)

How to use obsidian.md style internal links:
In the document, type [[\<page name\>]] to link to that page e.g. [[IAM]]

To display an alias for a link e.g. CNN instead of Convolutional Neural Network, first define an alias on the Convolutional Neural Network page:
```
---
aliases: [CNN]
---
```
Then use [[Convolutional Neural Networks|CNN]] to link to the Convolutional Neural Network page but only show the CNN alias

To link to a section on a page, use [[page#section]] e.g.
[[Recurrent Neural Networks#LSTM]]

This can be combined with an alias to display this section's link as RNN#LSTM by

[[Recurrent Neural Networks#LSTM|RNN]]

# Editing wiki on github (recommended)

Make commits to the main branch and they will automatically update on the site.  You can do this simply by clicking the edit icon on a page on the site.  If it asks you to login, contact me to make you a contributor

# Local wiki Editing

## Dependencies
* Python 3.4 and above
* [mkdocs](https://www.mkdocs.org/)
* [mkdocs-material](https://github.com/squidfunk/mkdocs-material)
* [mkdocs-roamlinks-plugin](https://github.com/Jackiexiao/mkdocs-roamlinks-plugin)

## How to install the wiki editing environment

Firstly, please clone this repository so you have all the files needed to edit the wiki.

```
git clone https://github.com/james-ralph8555/data-science-wiki
```

### Installing Python

You must install Python and pip (the python package manager) manually on your system.

* On Windows, download the Python installer from the Python website, which will install both `python` and `pip`
* On Linux, use your native package manager to install Python and pip (they are separate packages)
* On Mac, run `sudo easy_install pip` to install pip (assuming you're using Mac's built-in python distribution).

### 2 Install mkdocs

You must install mkdocs, a python tool which compiles the markdown files into the wiki. mkdocs comes with a built in server which gives you a live preview of your changes as you edit the markdown files. This makes editing easier and less error prone.

Install mkdocs and its plugins as below:
```
cd data-science-wiki
pip install -r requirements.txt
```


## Making and testing changes to the wiki

> **We recommend reading the mkdocs documentation before doing anything.** [**Click
here**](https://www.mkdocs.org/) to a more
in-depth
explanation on how to use it.

1. ``cd`` inside the repo (where `mkdocs.yml` is)
2. Run ``mkdocs serve`` to create a test environment at ``http://127.0.0.1:8000/`` . Since you will be doing this often, we have added `serve_website.bat` and `serve_website` (a shell script) which runs this command.
3. If you are satisfied with your changes, push the changes to github.  The site will be updated automatically within a minute.
4. If you need a local-only HTML version of the website run ``mkdocs build`` to convert the repository into a working website

### Generating the sitemap
To generate the sitemap on the home page, make sure you are in the root directory of this repo (data-science-wiki) and run
```
tree wiki | sed -E 's/── (.*)\.md$/── [[\1]]/' | sed 's/$/<br>/' | cat - > wiki/index.md
```
