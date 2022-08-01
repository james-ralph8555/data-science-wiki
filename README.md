# data-science-wiki
testing

The wiki is hosted at https://sozy.xyz/wiki

## Dependencies
* 3.4 and above
* [mkdocs](https://www.mkdocs.org/)
* [mkdocs-material](https://github.com/squidfunk/mkdocs-material)
* [mkdocs-roamlinks-plugin](https://github.com/Jackiexiao/mkdocs-roamlinks-plugin)

## How to install the wiki editing environment

Firstly, please clone this repository so you have all the files needed to edit the wiki.

```
git clone https://github.com/james-ralph8555/data-science-wiki
```

### 1. Installing Python

You must install Python and pip (the python package manager) manually on your system.

* On Windows, download the Python installer from the Python website, which will install both `python` and `pip`
* On Linux, use your native package manager to install Python and pip (they are separate packages)
* On Mac, run `sudo easy_install pip` to install pip (assuming you're using Mac's built-in python distribution).

### 2 Install mkdocs

You must install mkdocs, a python tool which compiles the markdown files into the wiki. mkdocs comes with a built in server which gives you a live preview of your changes as you edit the markdown files. This makes editing easier and less error prone.

Install mkdocs and its plugins as below:
```
cd data-science-wiki
pip -r requirements.txt
```


## Making and testing changes to the wiki

> **We recommend reading the mkdocs documentation before doing anything.** [**Click
here**](https://www.mkdocs.org/) to a more
in-depth
explanation on how to use it.

1. ``cd`` inside the repo (where `mkdocs.yml` is)
2. Run ``mkdocs serve`` to create a test environment at ``http://127.0.0.1:8000/`` . Since you will be doing this often, we have added `serve_website.bat` and `serve_website` (a shell script) which runs this command.
3. If you are satisfied with your changes, push the changes to github.
4. If you need a local-only HTML version of the website run ``mkdocs build`` to convert the repository into a working website

### Generating the sitemap
To generate the sitemap on the home page, make sure you are in the root directory of this repo (data-science-wiki) and run
```
tree wiki | sed -E 's/── (.*)\.md$/── [[\1]]/' | sed 's/$/<br>/' | cat - > wiki/index.md
```
