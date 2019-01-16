=================
Coding resources
=================

Python
-------

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
  - all lines :code:`:%s/foo/bar/g` 
  - this line :code:`:s/foo/bar/g`

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
A nice none in the field of molecular simulations is the 
`cookiecutter for computational molecular sciences python packages <https://github.com/MolSSI/cookiecutter-cms>`_ 

CI/CD
`````

Docker 
******

Pre-Commit 
``````````

Documentation 
`````````````
* `ReStructured Text Quickreference <http://docutils.sourceforge.net/docs/user/rst/quickref.html>`_: useful when writing sphinx docs

