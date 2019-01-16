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
* :code:`syntax enable` is probably self-explanatory
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
  
If you want to see a really crazy setup, check out 
`Damian Conway's vim setup <https://github.com/thoughtstream/Damian-Conway-s-Vim-Setup>`_. 
There you can also find how to create the `Star Wars intro in vim <https://github.com/thoughtstream/Damian-Conway-s-Vim-Setup/blob/master/plugin/SWTC.vim>`_. 

Commands I tend to forget
*************************

PyCharm
```````
PyCharm is the IDE I use for larger python projects, some useful features are:


Sublime
```````
Sublime is a lot faster than PyCharm and supports basically all languages. 


Development process
-------------------



