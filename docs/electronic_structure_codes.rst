===============================
Electronic Structure Codes
===============================

VASP
----

Creating input files
````````````````````
* `Pymatgen relax sets <http://pymatgen.org/_modules/pymatgen/io/vasp/sets.html>`_ are really useful as they also come with e.g. useful `MAGMON settings <https://github.com/materialsproject/pymatgen/blob/master/pymatgen/io/vasp/VASPIncarBase.yaml>`_ 


Common problems 
````````````````
* In my opinion, VASP is pretty silent when stopping a run altough not reaching 
  the convergence criteria. Double checking the forces is essential here.
* To avoid stack size errors, you might find it useful to set 
     ::

          ulimit -s unlimited

in your :code:`.bashrc`


cp2k
-----

Creating input files
````````````````````
* `pycp2k <https://github.com/SINGROUP/pycp2k>`_ makes it maybe a bit more easy to create input files


Quantum Espresso
-----------------

Creating input files
````````````````````

* There are some interesting developments coming from the ASE community, particularly interesting are the developments
  from `Johannes Voss <https://github.com/vossjo/ase-espresso>`_
  that allow one to use the ASE optimizers and also initialize finite-difference phonon calculations
  with the potential of a previous (undisplaced) calculation

