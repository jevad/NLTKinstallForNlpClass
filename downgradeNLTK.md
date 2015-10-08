# Backgrading NLTK
Our Professor informed us that he would like for us to use NLTK 2, not NLTK 3.

If you installed NLTK using any of the [instructions on the NLTK web site](http://www.nltk.org/install.html), [the instructions that I wrote](./README.md), a default pip installion or a default Anaconda or Miniconda installation, then you have installed either NLTK 3.0.5 or NLTK 3.0.3.  It doesn't make a difference whether you're using Windows, Linux or OS/X.  

Ideas for performing a backgrade appear below.

## Finding NLTK 2.x.
First, you have to find NLTK 2.x.  There are no links for NLTK 2.x on the NLTK web site, and no *obvious* links for NLTK 2.x on the PyPI web site.  

Here's where I found links to NLTK 2.x:

https://pypi.python.org/simple/nltk/ .  

https://github.com/nltk/nltk/releases .  (You might have click "Next" at the bottom of the page to get to 2.x links.)

### Here's how I went about finding the links to NLTK 2.x:  

In interest of "teaching a man to fish", here's how I knew where to find the links.  You can skip this section, however, and come back to it later if you find that you need to know.

_Searching on PyPI_:  By default, PyPI will only show you the most recent version of something.  So, for example, if you follow the "download" link on the NLTK web site, you'll end up here, https://pypi.python.org/pypi/nltk , which presently shows version 3.0.5 -- the most recent stable version.  Frustratingly, there is no link on that page to see a complete list which other versions of NLTK are available.  You could do a Google site-search, but there is no guarantee that it will give you a complete list.  Thankfully, there is a hack that works for now:  In the preceding URL, replace "pypi" with "simple", https://pypi.python.org/simple/nltk/ .  And, from there, you can browse, and download, all the NLTK versions that are on PyPI.  If you then want to see the notes associated with one of those versions, you replace "simple" with "pypi" and add the version number at the end.  So, if you want to see the notes for version 2.0.4, you enter a URL like this, https://pypi.python.org/pypi/nltk/2.0.5 . Note that the most recent version shown here is 2.0.5 -- I'll get back to that later.

_the official source code_:  In situations like this, it never hurts to track down the official source code, so you can see for sure if a version you've encountered was, in fact, an official release.  Open source projects are always looking for folks to help out, so you can usually find, on the project web site, an information page for software developers, which usually includes a link to the project's official source code repository.  For NLTK, information for developers is here, http://www.nltk.org/contribute.html , and that page links you to their GitHub source code repository, which is here, https://github.com/nltk/nltk .  The GitHub repository has a "Releases" tab, clicking on that, takes us here, https://github.com/nltk/nltk/releases, where we find a list of official releases.  You may have to scroll to the bottom and hit "Next" to get to the 2.x releases.  2.0.4 appears to be the last official 2.x release showing here, so I'm going to consider the 2.0.5 release on PyPI to be somewhat suspect and investigate.  It turns out that 2.0.4 cannot be installed with Pip, so Steve Bird, one of the authors of NLTK, created version 2.0.5 and posted it to PyPi (ref: https://github.com/nltk/nltk/issues/824 ).

## If you installed NLTK manually:
Download the source for the version you want, and install the new version the same way you did the old version.

## If you installed NLTK using Pip:
Check your currently installed version of NLTK:
```
pip list
```
It's probably 3.0.5.  To change it to 2.0.5:
```
pip uninstall nltk
pip install -Iv nltk==2.0.5
```
Run whatever tests you feel you ought to to give you confidence in the installation.

## If you installed NLTK using Anaconda or Miniconda:
