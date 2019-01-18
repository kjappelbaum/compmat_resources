=================
Coding 
=================

General 
-------
* Software developers who train for interviews use `Hackerrank <https://www.hackerrank.com/interview/interview-preparation-kit>`_ but it has nice problems if you just want to improve your computational thinking and coding skills in general
* The `Common-Sense Guide to Data Structures and Algorithms: Level Up Your Core Programming Skills <https://pragprog.com/book/jwdsal/a-common-sense-guide-to-data-structures-and-algorithms>`_, written by Jay Wengrow, is a fast and easy read to get an introductions to datastructures, time complexity and some important sorting and searching algorithms  

Python
-------

Jupyter notebooks on HPC environments
`````````````````````````````````````

Using configuration file
*************************

In some cases it can be useful to, instead of running the ipython kernel on the headnode, to just submit it
to computing node of cluster and then access the kernel from the browser (either from the headnode or your local machine).

You can achieve this by setting some things in your :code:`~/.jupyter/jupyter_notebook_config.py` file you can
create this file using :code:`jupyter notebook --generate-config`.

In this file you then can modify the following:

::

    c.NotebookApp.ip = '*'
    c.NotebookApp.open_browser = False
    c.NotebookApp.port = XXXXX

Where :code:`XXXX` is a number greater than 8888. You might also want to set a password instead of a token
(you can do this in the config file or by running :code:`jupyter-notebook password`).
In your submission script you can then add :code:`hostname` to print the hostname which you can then use to access
the notebook at :code:`hostname:XXXXX`. In some cases you might also want to hardcode  :code:`c.NotebookApp.ip` to
the ip of a particular compute node and then simply bookmark this address.


Using tunneling
***************
Add the following lines to your submission script

::
    unset XDG_RUNTIME_DIR
    NODEIP=$(hostname -i)
    NODEPORT=$(( shuf -i 8888-9999 -n 1))
    echo $NODEIP:$NODEPORT

    jupyter-notebook --ip=$NODEIP --port=$NODEPORT --no-browser

:code:`shuf -i 8888-9999 -n 1` is just to get a random port (binding to 0 and letting the OS is chose is better
practice, but this here is easier). You can then look into the output file which your
scheduler produced as it should contain :code:`NODEIP` and :code:`NODEPORT` which you can then use to
establish a tunnel connection from your local machine using

::

    ssh -N -L 8888:$NODEIP:$NODEPORT <username>@<machinename>

on your local machine you can now access the jupyter server at :code:`http://localhost:8888`.

Note that in both approaches the kernel will of course die after the walltime is exceeded.

Online
``````

C
--

Online
``````
* `Build your own lisp <http://www.buildyourownlisp.com/>`_ is a nice way to get
  started with C and learn about lisps 


Editors/IDEs
------------

VIM
```
Vim is a really powerful editor, but you need to spend some time learning and
configuring it. 

Configuration
*************

Some useful settings for the :code:`.vimrc` file are:

* syntax highlighting :code:`syntax enable` is probably self-explanatory
* search
  :: 

       set incsearch           " lookahead search
       set ignorecase          " in most cases I want to be case-insenstivie
       set smartcase           " unless i explicitely use uppercase
       set hlsearch            " highlight matches

* identations
  ::

       set tabstop=4           " number of spaces per <TAB>
       set expandtab           " convert <TAB> key-presses to spaces in insert mode
       set shiftwidth=4        " set a <TAB> key-press equal to 4 spaces

       set autoindent          " copy indent from current line when starting a new line
       set smartindent         " even better autoindent ('smart' insert after e.g. {) 

* Persistent undo
  ::

       if has('persistent_undo')
         " Save all undo files in a single location (less messy, more risky)...
         set undodir=$HOME/.VIM_UNDO_FILES

         " Save a lot of back-history...
         set undolevels=5000

         " Actually switch on persistent undo
         set undofile

       endif

* I am paranoid, I want to lose at max 10 keystrokes
  ::

     set updatecount=10

* If you do not want to type all the search replace syntax (vide infra) remap it 
  ::
     
     nmap  S  :%s//g<LEFT><LEFT>

  now you need to type only 
  ::
     
     SX/Y<CR>

  for global search/replace on all lines.


If you want to see a really crazy setup, check out 
`Damian Conway's vim setup <https://github.com/thoughtstream/Damian-Conway-s-Vim-Setup>`_. 
There you can also find how to create the `Star Wars intro in vim <https://github.com/thoughtstream/Damian-Conway-s-Vim-Setup/blob/master/plugin/SWTC.vim>`_. 

Plugins 
*******
* `schelpp <https://github.com/zirrostig/vim-schlepp>`_: makes it easier to move stuff in visual block
* `fatfinger <https://github.com/chip/vim-fat-finger>`_: corrects common misspellings

Commands 
*********
* Use :code:`$` to get to the end of the lines 
* Use different navigation levels :code:`b`, :code:`w`, :code:`{` and :code:`(`
* Search/Replace (:code:`g` means global)   
     
     * all lines :code:`:%s/foo/bar/g` 
     * this line :code:`:s/foo/bar/g`

PyCharm
```````
PyCharm is the IDE I use for larger python projects, some useful features are:


Sublime
```````
Sublime is a lot faster than PyCharm and supports basically all languages. 


Development process
-------------------
Starting a project
``````````````````
The easiest way to start a (python) project is to use a `cookiecutter <https://github.com/audreyr/cookiecutter>`_ 
that creates the basic project structure and also some configuration files for you. 
A nice one in the field of molecular simulations is the 
`cookiecutter for computational molecular sciences python packages <https://github.com/MolSSI/cookiecutter-cms>`_ 

CI/CD
`````

Docker 
******
On HPC environments, where you don't have root rights, `singularity <https://www.sylabs.io/docs/>`_ might be a
way to go. There is also a `image to convert singularity images to docker images <https://github.com/singularityware/docker2singularity>`_

Git(hub)
********


Pre-Commit 
``````````

Documentation 
`````````````
* `ReStructured Text Quickreference <http://docutils.sourceforge.net/docs/user/rst/quickref.html>`_: useful when writing sphinx docs

