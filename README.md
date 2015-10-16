# Setting up Python and NLTK on Windows for the NLP Class

##### Table of Contents  
[Audience](#audience)  

[Initial Comments](#initial)  

[Option 1:  The Easiest Way to Set Up Python and NLTK on Windows](#easiest) -- use a prepackaged "scientific" distribution -- if you don't already have Python installed, and if you don't care whether or not you use the standard Python installer, this is recommended. 

[Option 2:  Using the Standard Python Installer and Pip](#stpip) -- if you already have Python installed or if you want to use the standard Python installer, take a look at these instructions.

[Option 3: Use Miniconda or Anaconda to set up an Environment](#condawithenvironments") -- use environments like all the cool kids.  

[More Options:  Coming Soon (if I have time):  Using virtual environments -- not quite as easy but might be worth the extra effort.](#tbd)  
* ([DONE](#condawithenvironments) Use Miniconda or Anaconda to set up a virtual environment for the class -- this is the way I have things set up.
* Use the "standard tools", Pip and virtualenv, to set up a virtual environment for the class -- this is the way to go if you want to use a Python version that you've already installed (say, by downloading and installing the one from http://www.python.org/ ). 

[Special Notes](#notes)
* How to get out of the Python prompt
* non-ASCII characters

[Setting the System PATH](#setpath) -- if you want to add a directory to your system PATH.

<a name="audience"/>
## Audience
This page is to help my classmates taking an online NLP class that uses Python and NLTK.  Some of us have had difficulty getting Python and NLTK set up properly.  If this is useful to anyone else, so much the better.

<a name="initial"/>
## Initial Comments
Reading through the class forum posts, I noticed that some people are installing NLTK and Python manually (i.e., the hard way) instead of using Pip or one of the prepackaged "scientific" Python distributions.  There are sometimes good reasons for setting up things the without using Pip or one of the prepackaged distributions; however, I couldn't think of why people in our class would be going out of the way to do things the hard way.  Then I finally read the NLTK installation instructions:

---- 
![NLTK Installation Instructions](/images/NLTK_instructions.png)

---- 
Suddenly, it all made sense:  People were doing things the hard way because they were just following instructions!

You'll note that the instructions for Mac and Unix users have you use Pip to install packages; whereas, the instructions for Windows users have you doing everything manually and don't really give you much guidance as to how to make that happen -- if you're a progammer-type, you can figure it all out fairly quickly, but, if you're not....  

You'll also notice that the only people posting about installation problems on the class forum are Windows users.  

What you'll find here are some easier ways to get things installed on Windows.

(By the way, let this be a lesson:  Many things involving software development and data analysis are better supported when you're not using Windows.  Personally, I prefer to use OS/X or Linux for this sort of thing.)

<a name="easiest"/>
## Option 1:  The Easiest Way to Set Up Python and NLTK on Windows
* Use a pre-packaged "scientific" distribution.

The easiest way to set up Python and NLTK on Windows is to use Enthought Canopy, https://www.enthought.com/products/canopy/ , or Continuum Analytics Anaconda, http://docs.continuum.io/anaconda/index .  Both are prepackaged "scientific" distributions that come with a number of Python libraries, such as NLTK and NumPy.  The libraries in each distribution are tested to work well with each other.  These distributions are perfect for people working in the areas of machine learning, language processing, text processing or data science who wish to primarily concentrate on their specific fields of expertise and not on being expert Python programmers (although, they're good environments for expert Python programmers too).  

Both come with instructions, but, since we've had bad luck with instructions so far, here are my instructions for one of them (Anaconda):

1. Download Anaconda for Python 2.7 from https://www.continuum.io/downloads#_windows .  Get the version that matches your processor.  This is a 335 MB download, so you have time to grab a cup of coffee if you're on a slow network -- resist the temptation to watch cat videos while you're waiting as that will chew up your bandwidth (unless, of course, you planned ahead and have already downloaded cat videos just for this purpose).  

2. Follow the instructions for installing Anaconda.
  * **Make sure you select "Add Anaconda to the system PATH environment variable" when you have the option to do so.** (This will save you the trouble of adding it to the PATH later.)  

That's it.  You're actually done at this point because Anaconda contains NLTK along with plenty of other packages (http://docs.continuum.io/anaconda/pkg-docs ). However, I recommend a couple of other steps:

* Open a Windows command prompt and run the following commands:
```
conda update conda
conda update --all
conda list python
conda list nltk
conda list numpy
conda list scipy
conda list scikit-learn
```  
The first command will update conda, the package manager that comes with Anaconda.  The second command will update all the installed packages to the latest appropriate version.  The remaining commands will verify that NLTK and the other programs we need for this class are installed and will show you the version (If you want to see ALL the packages that are installed, just run `conda list` without any additional arguments.).

Make sure that the versions are correct, per our Professor's instructions.  When I just did this to test it, all of the versions were acceptable except for scikit-learn.  To downgrade a package, in this case, scikit-learn, to a specific version, you do the following:
```
conda uninstall scikit-learn
conda install scikit-learn=0.15
```

* To verify that everything is working properly:
  1. run python
  2. check to make sure the python version is correct
  3. from the python shell, run the following commands:
  ```
  import nltk
  nltk.download()
  ```
  You should see a Graphical User Interface (GUI) pop up.  If you don't want to download any of the collections, just close the window.  I don't know if we'll need any of the downloads for class or not.  You will need some of them if you want to follow the exercises in Natural Language Processing with Python (see section 1.2, http://www.nltk.org/book/ch01.html , for more information).  If something doesn't work or doesn't look right, post a message on the class forum.

<a name="stpip"/>
## Option 2:  Using the Standard Python Installer and Pip

We're going to use Pip, as shown in the Mac/Unix instructions on the NLTK web site (see picture above), to install NLTK and other libraries on Windows.  Pip will make our life easier because it will find libraries and so forth for us.  And, besides, why should the Mac and Unix users have all the fun?

First, we need to download and install Python (if you have not already done so).  The Professor wants to use Python 2.7, so get the latest version of Python 2.7, so go here, https://www.python.org/downloads/ , find the latest version of Python 2.7, and click on the download link.  You'll see a bunch of choices.  For these instructions, we're going to choose the 32-bit MSI installer (which you can identify as the MSI installer that is NOT 64-bit).  There's nothing wrong with the 64-bit version, and you can make the 64-bit version work if you wish, but, as far as I can tell, most of you have already installed the 32-bit version (perhaps due to the warning on the NLTK instructions), so I'm using the 32-bit version here.  

You'll be given some options when you install Python.  
* For these instructions, I'm assuming that you installed Python in C:\Python27 (That's the "Install for all users option".).  **If you installed it somewhere else, that's fine, but you'll need to modify the paths that appear in the rest of these instructions to reflect your installation.**
* **On the "Customize Python" page, you may wish to choose to "Add python.exe to Path".**  This will add the directory containing Python to your system PATH, which will allow you to run Python without typing in the full path name.  For the remainder of these instructions, I'm assuming you've done that -- if you haven't, then you'll need to type in the full path whenever you run python or pip.  If you don't add them to your system PATH and then change your mind, there are instructions below on how to [update the system PATH manually](#setpath).

OK.  So now we have Python installed, and we have Python and some useful scripts in our system PATH (maybe -- if you chose to do that).  We're in the home stretch!

Open a Windows command prompt and use pip to install stuff:
```
pip install --upgrade "nltk<3.1,>=3.0"
```
Pip isn't magic -- it needs to get the packages from somewhere, so, if you're not hooked up to the internet, you'll get an error.  (There is a way to have Pip install packages from a local repository -- you can google about that if you're interested.)  

Pip does, however, do quite a bit of work for you.  Notice how, when you installed NLTK, Pip checked to see if other libraries also needed to be installed (like the six library that gave some folks difficulty)!  The `--upgrade` flag tells Pip to update NLTK if it is already installed but not at the latest version.  If we want to see what libraries have been installed by Pip, we use the `list` target:
```
pip list 
```

Now let's install NumPy:
```
pip install --upgrade "numpy>=1.6.1"
```
The NumPy installation probably printed out a bunch of warning and error messages.  By default, Pip gets it's packages from the PyPI site, https://pypi.python.org/pypi , and the NumPy package there is expecting some stuff I didn't have and you probably don't have either.  Oh, no!  What do we do?

There are several possible workarounds, so the first thing you should do is google to see how other people recommend you solve the problem.  You'll run into less problems if you let other folks discover, through trial and error, the best solution for you.  Some Google hits from StackOverflow, http://stackoverflow.com/ , proved to be useful, and the consensus seemed to be to use the installation package from the Gohlke collection, http://www.lfd.uci.edu/~gohlke/pythonlibs/ .  (You will NOT ALWAYS want to use the libraries from the Gohlke collection because they're sometimes less stable than other sources (see Gohlke's warning at the top of the page), so check on the web first and see what other developers are saying, but the Gohlke collection is a great resource to keep in mind.)  The versions of NumPy available in the Gohlke collection are listed on the page here, http://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy .  Based on the notes there and things I read elsewhere, I recommend choosing one of the MKL versions.  Since we installed 32-bit Python, we want a version with "win32" in the name, and since we installed Python 2.7, we want a version with "cp27" in the name.  At present, the newest version that fits both those requirements is numpy-1.9.3+mkl-cp27-none-win32.whl.  Downlaod that file.  

Pip installation package files are known as "wheel files" and usually have the extension, ".whl".  After you've downloaded the wheel file, install the package with pip:
```
pip install Downloads\numpy-1.9.3+mkl-cp27-none-win32.whl
```
(Modify the path to match wherever you've downloaded the wheel file.)

Now let's install SciPy:
```
pip install --upgrade "scipy>=0.9"
```
You'll probably run into the same problem you did with NumPy.  Once again, the Gohlke Collection, looks like a good solution.  You can find the file here, http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy .  
```
pip install ..\Downloads\scipy-0.16.0-cp27-none-win32.whl
```

Now let's install scikit-learn:
```
pip install "scikit-learn<0.16,>=0.15.2"
```

OK.  So now we've installed, Python, NLTK, NumPy, SciPy and scikit-learn.  Let's start up Python by entering `python` at a Windows command prompt.  Then we'll enter some Python statements to try out NLTK to make sure things are working -- we'll work through the first couple of sections of _Natural Language Processing with Python_, http://www.nltk.org/book/ch01.html (so look at the book at that link if you're wondering where these statements come from -- I'm going to skip some of the statements, here, but you might want to try out all of them):
```
from __future__ import division
import nltk
nltk.download()
```
If everything is working correctly, this should bring up a Graphical User Interface (GUI).  Since we're working through the stuff in the book, choose to download the "book" collection.  Close the window when the download has completed and your Python command prompt will return.
```
from nltk.book import *
text4.dispersion_plot(["citizens", "democracy", "freedom", "duties", "America"])
```
Oh, no!  Another error.  Reading the error message, it looks like Matplotlib is missing.  What to do?  In situations like this, you'll often find that you can just `pip install missing-library-name`.  Open up another **Windows** command prompt and give it a try:
```
pip install matplotlib
```
Now let's go back to the window with our Python prompt and try it again:
```
text4.dispersion_plot(["citizens", "democracy", "freedom", "duties", "America"])
```
And it works!  Hooray!  :sparkles: :rocket: :sparkles:  You're on your way to a happy and productive future with Python and Pip!

To learn more about your new friend, Pip, see the official documentation, https://pip.pypa.io/en/stable/ .

<a name="condawithenvironments"/>
## Option 3: Use Miniconda or Anaconda to set up an Environment
This is actually the way I have things set up.

Download and install either Anaconda, https://www.continuum.io/downloads , or Miniconda, http://conda.pydata.org/miniconda.html .  The difference between the two is that Miniconda is a fairly bare-bones Python development environment; whereas, Anaconda includes many scientific computing libraries that work well together, resulting in a full scientific computing and data analysis environment.  For our purposes, it doesn't make much difference which one you choose.  And, for that matter, it actually doesn't make much difference if you install the Python 2 version or the Python 3 version.  If you're on a very slow internet connection, Miniconda is much smaller than Anaconda, and, also, you'll save yourself the trouble of downloading Python 2.7, when you create your environment, if you choose the Python 2 version, since it will already be on your machine.

Documentation for how to use the `conda` tool may be found here, http://conda.pydata.org/docs/install/quick.html .  There is also a useful cheat sheet, http://conda.pydata.org/docs/_downloads/conda-cheatsheet.pdf .

Once you have installed Anaconda or Miniconda, update the system:
```
conda update conda
conda update --all
```
Now, create your enviroment:
```
conda create -n nlpclass python=2.7 nltk=3.0 numpy scipy scikit-learn=0.15
```
You can read the conda documentation for full information, but, basically, what this command does, is:
* It creates an environment named, nlpclass.  (There is nothing special about that name -- feel free to use whatever name you wish).
* It uses Python 2.7.x as the base Python version for this environment.
* At the same time, it also installs NLTK 3.0.x, numpy (latest version), scipy (latest version) and scikit-learn 0.15.x.\
Actually, I added a few additional libraries, so I created the environment with this command:
```
conda create -n nlpclass python=2.7 nltk=3 numpy scipy scikit-learn=0.15 matplotlib jupyter networkx
```
Once you've created the environment, you need to activate it in order to use it:
```
activate nlpclass
```
Note that your command prmopt is now preceded with `[nlpclass]` (or whatever name you chose).  If you examine your system PATH (`echo %PATH%`), you'll see that, in this environment, environment-specific directories are at the top of the PATH.  

Let's verify that the libraries we want are in this environment:
```
conda list
```
Check the version numbers against those provided by our Professor.

When you're done working in this environment, you can deactivate it by running the deactivate command:
```
deactivate
```

<a name="tbd"/>
## Coming Soon (if I have time):  Some other ways to set things up -- not quite as easy but probably worth the extra effort.
If you want to be able to run multiple versions of python on your computer or have custom library setups for individual projects, you'll want to use virtual environments -- this is more useful than you might think.  You can create virtual environments using conda, which comes with Miniconda and Anaconda, or with virtualenv, which you can install with Pip.  I'll try to get around to adding some instructions in this section for how to do that.  In the meantime, you can just google it.
* [Already done](#condawithenvironments): Use Miniconda or Anaconda to set up an environment for the class -- this is the way I have things set up.
* TBD: Use the "standard tools", pip and virtualenv, to set up an environment for the class.

<a name="notes"/>
## Special Notes
* _How to get out of the Python prompt_:  enter `quit()`.
* _non-ASCII characters_:  Prior to Python 3, by default, Python strings used ASCII encoding.  ASCII was created to encode transmissions from circa-1960 U.S. teletype machines.  At the time, ASCII was considered a big advance because it could encode BOTH uppercase and lowercase letters.  Folks were so happy that they could send BOTH uppercase and lowercase characters that they didn't even mind that accented characters, non-Latin characters et cetera were not encodable in ASCII.  As a result, if your machine name, user name, home directory name or anything like that has a non-ASCII character in it, you may have difficulty running Python 2.  

<a name="setpath"/>
## Setting the System PATH
OK.  So we have Python installed.  Look at the installation in Windows Explorer.  The top directory of the installation will contain python.exe (among other things), and, in that directory, there will be a Scripts directory that will contain pip.exe (among other things).  

Open a new Windows command prompt and enter:
```
echo %PATH%
```
Do you see BOTH the top directory and and the Scripts in your path?  If not, and if you want them to be in your path, you'll need to modify your system PATH, so you can run the programs in these directories without having to type in the full path to them every time.  How you do that will vary a bit depending on which version of Windows you're using, but, here's how it works on Windows 7: 

(For these instructions, I'm assuming that your top directory is C:\Python27 and your Scripts directory is C:\Python27\Scripts.  Note that your directories may be different.  In fact, if you're using Miniconda or Anaconda, they're almost certainly different.)

1. Go to Control Panel -> System -> Advanced system settings.  
2. Click on "Environment Variables..." to open up the environment variables editor.  
3. In the "System variables" section (if you installed Python for "All Users") or in the "User variables" section (if you installed Python just for yourself), click on the PATH variable and then click "Edit...".  
4. VERY CAREFULLY add C:\Python27 (if it is missing) and C:\Python27\Scripts (if it is missing) to your PATH.  It is important to know and remember that the elements of the PATH are separated by semicolons, `;`, but not by spaces.  The PATH is read in order by the operating system, so, if there are two Python installations on your computer, the one that appears first in the PATH will be the one that will be used (in most cases -- some programs, especially IDEs, have a different way of finding other programs, but we won't worry about that for now).  
5.  When you're satisfied that you have everything as it should be, keep clicking "OK" to save and back out.  
6.  Close the Windows comamnd prompt you were using, open up a new one, enter `echo %PATH%` and verify that your change happened as expected.


