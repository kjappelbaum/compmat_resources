===============================
Electronic Structure Codes
===============================


General
-------
* If you want to know something about the :math:`\Delta` value (RMS energy difference between equations of state,
  as described in `Reproducibility in density functional
  theory calculations of solids <http://science.sciencemag.org/cgi/rapidpdf/351/6280/aad3000?ijkey=teUZMpwU49vhY&keytype=ref&siteid=sci>`_) you should got to https://molmod.ugent.be/deltacodesdft.
* There was a similar effort for pseudopotentials. The approach is described in the article `Precision and efficiency in solid-state pseudopotential calculations
  <https://www.nature.com/articles/s41524-018-0127-2>`_ and the library is accessible in the `MaterialsCloud <https://www.materialscloud.org/discover/sssp/table/efficiency>`_.
* For phonon calculations, there are some nice developments from Johannes Voss:
	
	* In `ase-espresso <https://github.com/vossjo/ase-espresso/wiki>`_ he initializes displaced calculations in the finite difference method with the KS potential of an undisplaced calculation.
	* In `another work <http://orbit.dtu.dk/files/4807182/O1freepaper.pdf>`_, he uses charge densities from the ground state to construct an interatomic potential which is then used to construct an approximate Hessian which can be useful for quick estimates of e.g. decomposition temperatures (but it fails for temperatures above the maximum phonon energy and it is :math:`\Gamma`-point only)
* `Elate from FX. Coudert <http://progs.coudert.name/elate>`_ is a nice python module to analze elastic tensors.
* The Kullik group has some useful tutorials http://hjkgrp.mit.edu/Tutorials
* For the calculation of reactions, a `review by Ryu et al. contains some useful starting points <https://pubs.acs.org/doi/abs/10.1021/acs.organomet.8b00456>`_
* For using slab calculations `Fionrentini is a classic on of to extract surface energies <https://iopscience.iop.org/article/10.1088/0953-8984/8/36/005/meta>`_. If you do this, you probably also want to look at the `dipole correction <http://www.phys.ufl.edu/~majewski/nqr/paper/dft/1998-bengston-Dipole-correction-surface-supercells.pdf>`_ from Bengtsson
* `Wang et al. <https://www.nature.com/articles/npjcompumats20166.pdf>`_ give a good overview over tools and methods for phonon calculations
* If you use PBC, you should also consider `Payne's paper <http://www.phys.ufl.edu/~majewski/nqr/paper/dft/1995-Makov-Payne_Periodic-boundary-conditions-ab-initio-calculations.pdf>`_

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


AiiDA
-----
Though not an electronic structure code, it fits best into this category. 

Get Workchain results
``````````````````````

.. code::

  qb.append(WorkCalculation, filters={
       'attributes._process_label': '<workchain_classname>',

   })

:code:`qb.all()` will then return a list of list, where the results can be accessed via :code:`workcalc.out.result.get_attr('<attr_name>')`