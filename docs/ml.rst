=================
Machine Learning
================= 

Machine Learning is getting a central part of our field. There is a `huge curated list with all kinds
of ML frameworks and packages <https://github.com/josephmisiti/awesome-machine-learning>`_

The most recent advances can be found with paper and code on `paperswithcode <https://paperswithcode.com/>`_ 

Online Courses
--------------


Articles
--------
* `Model Evaluation, Model Selection, and Algorithm Selection in Machine Learning <https://arxiv.org/abs/1811.12808>`_
  focusses on classification problems but still is a great resource of how to perform performance evaluations (regarding multiple testing remember the probability for type-1 error for multiple testing is
  :math:`1-(1-\alpha)^n`, where :math:`n` is the number of test and :math:`\alpha` the type-1 error rate of the single test).
* `A high-bias, low-variance introduction to Machine Learning for physicists <https://arxiv.org/abs/1803.08823>`_ is a nice introduction to core ML techniques. 

Books
-----



Python Packages
---------------
* `shap <https://github.com/slundberg/shap>`_ : Shapely values are a nice way 
  to bring interpretability to Machine Learning. The 
  `intepretable machine learning book <https://christophm.github.io/interpretable-ml-book/shapley.html>`_
  gives an overview over this and other methods for interpretable ML 
* holoviews 
* `pandas profiling <https://github.com/pandas-profiling/pandas-profiling>`_ gives some more useful information
  for exploratory data analysis than :code:`df.describe()` 
* `feature selector <https://github.com/WillKoehrsen/feature-selector>`_
  is a useful package for intial steps of feature engineering 
* If you already have (ASE) trajectories around, then `AMP <https://amp.readthedocs.io/en/latest/>`_ can be nice
  to build a ML model based on them
* `QML <http://www.qmlcode.org/>`_ has a similar goal. It has efficient implementations to calculate representations
  and kernels
* `matminer <https://github.com/hackingmaterials/matminer>`_ is really useful to compute common descriptors
* `Edward <http://edwardlib.org/>`_ is a nice package for probabilistic modelling like bayesian neural nets.
* `PyMC3 <https://docs.pymc.io/>`_ is a popular package for probabilistic programming
* `missingno <https://github.com/ResidentMario/missingno>`_ is a nice package for analzying missing data
* `pyGAM <https://github.com/dswah/pyGAM>`_ is a python implementation of `generalized additive models <https://web.stanford.edu/~hastie/Papers/gam.pdf>`_ (a nice overview of GAMs is in a `blogpost from Kim Larsen <https://multithreaded.stitchfix.com/blog/2015/07/30/gam/>`_)
* `eli5 <https://eli5.readthedocs.io/en/latest/overview.html>`_ is a nice package visualize the explanations of mostely white-box models. 
* `i like to cycle my learning rates <https://github.com/bckenstler/CLR>`_ . Related is the great idea of `snapshot ensembles <https://openreview.net/pdf?id=BJYwwY9ll>`_  I hope to find time at some point to generalize the `keras implemtation <https://github.com/titu1994/Snapshot-Ensembles>`_ a bit more. This blogpost gives a great overview https://www.jeremyjordan.me/nn-learning-rate/
* something that I starting using way to late is tensorboard, in keras it is simply this callback
  :: 

    tbCallBack = keras.callbacks.TensorBoard(log_dir='logs', 
                                         histogram_freq=0, write_graph=True, 
                                         write_images=True)

  followed by 

  ::

    tensorboard --logdir logs

  to actually start tensorboard. 
* Magpie is not only a `brid <https://en.wikipedia.org/wiki/Magpie>`_ but also `a ML framework for inorganic materials <https://www.nature.com/articles/npjcompumats201628>`_ 
* `PyOD <https://github.com/yzhao062/pyod>`_ contains loads of different tools for outlier detection
* `tpot is a powerful way to optimize complete ML pipelines <https://github.com/EpistasisLab/tpot>`_ 
* `Everyone knows it: Adanet by google <https://github.com/tensorflow/adanet>`_ 

Various trivia
----------------

* An underappreciated measure of centreal tendency is the trimean (:math:`TM`)

	.. math:: 
		
		TM = \frac{Q_1 + 2Q_1 + Q_3}{4},

  where :math:`QM_2` is the median and :math:`Q_1` and :math:`Q_2` are the quartiles. 

		"An advantage of the trimean as a measure of the center (of a distribution) is that it combines the median's emphasis on center values with the midhinge's attention to the extremes." — Herbert F. Weisberg, Central Tendency and Variability. 

* It is quite useful to keep the following `nomogram <https://commons.wikimedia.org/wiki/File:P-value_nomograph_for_Bayesian_posterior_estimation.jpg>`_ in mind
	
	.. image:: fig/P-value_nomograph_for_Bayesian_posterior_estimation.jpg
	    :width: 500px
	    :align: center
	    :alt: P value nomogram

  
  This is directly connected to 
  	 	"Extraordinary claims require extraordinary evidence" -- Carl Sagan/Laplace

* A nice visualization of the famous `Ioannidis paper <https://journals.plos.org/plosmedicine/article?id=10.1371/journal.pmed.0020124>`_ is this `RShiny app <http://shiny.ieis.tue.nl/PPV/>`_
* A quite interesting discussion of the variance in the output function is reduced by adding more parameters to a (ensembled) network which then leads to a lower generalization error. They also provide a discussion of a divergence of the error at :math:`N^*` for networks without regularization. Preprint version is on `arXiv:1901.01608v3 <https://export.arxiv.org/pdf/1901.01608>`_
	
	.. image:: fig/generalization_error_parameters.jpg
		:width: 500px
	   	:align: center
	   	:alt: Measured generalization error as a function of the number of parameters (arXiv:1901.01608v3)

* I find `dilated convolutional NNs <https://arxiv.org/pdf/1511.07122.pdf>`_ to be quite a interesting way to increase the perceptive field. Ferenc Huszár gives another description in terms of `Kronecker factorizations of smaller kernels <https://www.inference.vc/dilated-convolutions-and-kronecker-factorisation/>`_ 
* `Spatial dropout <https://arxiv.org/pdf/1411.4280.pdf>`_ is quite interesting to make dropout work better on spatial correlations. 
* `Jensen's paper about GA for logP optimization <https://chemrxiv.org/articles/Graph-based_Genetic_Algorithm_and_Generative_Model_Monte_Carlo_Tree_Search_for_the_Exploration_of_Chemical_Space/7240751>`_ and also a recent work from `Berend Smit's group <https://www.nature.com/articles/s41467-019-08483-9>`_ are reminders that we shouldn't forget good old techniques such as GA. 