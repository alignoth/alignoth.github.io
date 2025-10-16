====================================================================
Alignoth: Create portable alignment plots from bam files
====================================================================

A tool for creating alignment plots from bam files. The generated `vega-lite <https://vega.github.io/vega-lite/>`_ plots are written to stdout per default.
An example of a generated plot can be seen `here <http://htmlpreview.github.io/?https://github.com/koesterlab/alignoth/blob/main/examples/plot.html>`_.
The name alignoth is derived from the visualized **align**ments combined with the star **alioth** (usage of vega plots).

Alignoth supports an interactive mode that can be activated by simply executing it without any arguments (i.e. ``alignoth``).
This launches a wizard that guides you through selecting input files, defining the region of interest, and choosing between an interactive HTML output or a Vega-Lite specification.

.. toctree::
    installation
    usage
    embedding
