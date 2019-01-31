=========
Plotting
=========

Pandas
-------
Recently, I found that pandas has a lot of nice plotting tools builtin which I do not use often enough:

* The autocorrelation plot is nice to analyze time series (e.g. simulation trajectories)
* Andrews curves are a good waz to analyze multidimensional datasets
* The bootstrap plot gives you information about the uncertainty of the statistics you get from pandas


Bokeh
------

Altair
------
The `Altair <https://altair-viz.github.io/>`_ library is interesting as it builds on D3 (and allows you to generate :code:`.json` for VEGA or :code:`.html` outputs) whilst being a easy to use, high-level and declerative python library.
It is relatively easy to build `coupled interactive plots <https://altair-viz.github.io/gallery/seattle_weather_interactive.html>`_.


Holoview
--------
* `hvplot <https://hvplot.pyviz.org/index.html>`_ offers a even more high-level api and is useful to get e.g. interactive
  pandas plot without memorizing new commands. I particularly like :code:`hvplot.scatter_matrix(df, c='<column_name>')`
