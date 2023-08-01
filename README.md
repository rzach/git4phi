git4phi
=======

Git for Philosophers

A basic introduction to the revision control system Git for non-programmers, specifically for using Git as a way to collaborate on document writing.

The guide is written in Markdown, the file is git4phi.md, and [can be read here](https://github.com/rzach/git4phi/blob/main/git4phi.md). You can download the latest release, including a printable PDF version, [here](https://github.com/rzach/git4phi/releases)

It is written by [Richard Zach](http://richardzach.org)

You should feel free to copy & use this as long as you abide by the [CC-BY license](LICENSE.md).

The default branch has been renamed to `main`. If you have cloned this
repository before this change, you will have to do this in your local
repository:
```
git branch -m master main
git fetch origin
git branch -u origin/main main
git remote set-head origin -a
```