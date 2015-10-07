# Setting up Python and NLTK on Windows for the NLP Class

##### Table of Contents  
[Audience](#audience)  

[Initial Comments](#initial)  

[The Easiest Way to Set Up Python and NLTK on Windows](#easiest)  

[Coming Soon (if I have time):  Some other ways to set things up -- not quite as easy but probably worth the extra effort.](#tbd)  
* Use Miniconda or Anaconda to set up an environment for the class.
* Use the "standard tools", pip and virtualenv, to set up an environment for the class. 


<a name="audience"/>
## Audience
This page is to help my classmates taking the Coursera NLP class.  Some of us have had difficulty getting Python and NLTK set up properly.  If this is useful to anyone else, so much the better.

<a name="initial"/>
## Initial Comments
Reading through the class forum posts, I noticed that some people are installing NLTK and Python manually (i.e., the hard way) instead of using Pip or one of the prepackaged "scientific" Python distributions.  I assumed that they _wanted_ to do things the hard way (there are sometimes good reasons to do so), then I noticed the following instructions on the NLTK web site:

---- 
![NLTK Installation Instructions](/images/NLTK_instructions.png)

---- 
Suddenly, it all made sense:  They were doing things the hard way because they were just following instructions!

You'll note that the instructions for Mac and Unix users have you use Pip to install packages; whereas, the instructions for Windows users have you doing everything manually.  What you'll find here are some easier ways to get things installed on Windows.

<a name="easiest"/>
## The Easiest Way to Set Up Python and NLTK on Windows
The easiest way to set up Python and NLTK on Windows is to use Enthought Canopy, https://www.enthought.com/products/canopy/ , or Continuum Analytics Anaconda, http://docs.continuum.io/anaconda/index .  Both are prepacked "scientific" distributions that come with a number of Python libraries, such as NLTK and NumPy.  The libraries in each distribution are tested to work well with each other.  These distributions are perfect for people working in the areas of machine learning, language processing, text processing or data science who wish to primarily concentrate on their specific field of expertise and not on being an expert Python programmer (although, they're great environments for expert Python programmers too).  Both come with instructions, but, since we've had bad luck with instructions so far, here are my instructions for one of them (Anaconda):

1. Download Anaconda for Python 2.7 from https://www.continuum.io/downloads#_windows.  Get the version that matches your processor.  This is a 335 MB download, so you have time to grab a cup of coffee if you're on a slow network -- resist the temptation to watch cat videos while you're waiting as that will chew up your bandwidth (unless, of course, you planned ahead and have already downloaded cat videos just for this purpose).  

2. Follow the instructions for installing Anaconda.
  * **Make sure you select "Add Anaconda to the system PATH environment variable" when you have the option to do so.** (This will save you the trouble of adding it to the PATH later.)  

That's it.  You're actually done at this point because Anaconda contains NLTK along with plenty of other packages (http://docs.continuum.io/anaconda/pkg-docs ). However, I recommend a couple of other steps:

* Open a Windows command prompt and run the following two commands:
```
conda update conda
conda update --all
conda list nltk
```  
The first command will update conda, the package manager that comes with Anaconda.  The second command will update all the installed packages to the latest appropriate version.  The third command will verify that NLTK is installed and will show you the version (If you want to see ALL the packages that are installed, just leave off the "nltk" -- a full package list for Anaconda, with the packages that should be installed by default marked, may be found here:  http://docs.continuum.io/anaconda/pkg-docs .).  

* To verify that everything is working properly (post a help query on the class forum if you get an error or if something doesn't look right):
  1. run python
  2. check to make sure the python version is correct
  3. from the python shell, run the following commands:
  ```
  import nltk
  nltk.download()
  ```
  You should see a Graphical User Interface (GUI) pop up.  If you don't want to download any of the collections, just close the window.  I don't know if we'll need any of the downloads for class or not.  You will need some of them if you want to follow the exercises in Natural Language Processing with Python (see section 1.2, http://www.nltk.org/book/ch01.html , for more information).

<a name="tbd"/>
## Coming Soon(if I have time):  Some other ways to set things up -- not quite as easy but probably worth the extra effort.
* Use Miniconda or Anaconda to set up an environment for the class.
* Use the "standard tools", pip and virtualenv to set up an environment for the class.
