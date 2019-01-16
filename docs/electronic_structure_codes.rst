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


