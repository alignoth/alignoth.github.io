.. _usage:

*****
Usage
*****

.. code-block:: bash

    alignoth

To activate the interactive mode guiding you through the process of creating an alignment plot.

.. code-block:: bash

    alignoth -b path/to/my.bam -r path/to/my/reference.fa -g chr1:200-300 > plot.vl.json

To directly generate a plot in svg, png or pdf format we advice using the `vega-cli <https://vega.github.io/vega/usage/#cli>`_ and `vega-lite-cli <https://vega.github.io/vega-lite/usage/compile.html#cli>`_ packages:

.. code-block:: bash

    alignoth -b path/to/my.bam -r path/to/my/reference.fa -g chr1:200-300 | vl2vg | vg2pdf > plot.pdf

To generate an interactive view within an html file use `--html` and capture the output to a file:

.. code-block:: bash

    alignoth -b path/to/my.bam -r path/to/my/reference.fa -g chr1:200-300 --html > plot.html

Arguments
~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 15 10 60 15

   * - argument
     - short
     - explanation
     - default
   * - bam-path
     - -b
     - The bam file to be visualized.
     -
   * - reference
     - -r
     - The path to the reference fasta file
     -
   * - region
     - -g
     - Chromosome and region for the visualization. Example: 2:132424-132924
     -
   * - around
     - -a
     - A chromosome and a base position that will define the region that will be plotted starting 500bp before and end 500bp behind the given position. Example: 2:17348
     -
   * - highlight
     - -h
     - Named intervals or single base positions that will be highlighted in the visualization. Example: myinterval:132400-132500 or myvariant:132440
     -
   * - vcf
     - -v
     - Path to a VCF file. Variants from the VCF file will be highlighted in the resulting plot similar to the highlight option.
     -
   * - bed
     - 
     - Path to a BED file. Regions from the BED file will be highlighted in the resulting plot similar to the highlight option.
     -
   * - plot-all
     - -p
     - Plot all reads in the given region. We advise to only use this command for small bam files with a single target.
     - false
   * - max-read-depth
     - -d
     - Set the maximum rows of reads that will be shown in the alignment plots
     - 500
   * - max-width
     - -w
     - Set the maximum width of the resulting alignment plot
     - 1024
   * - output
     - -o
     - If present, data and vega-lite specs of the generated plot will be split and written to the given directory
     -
   * - data-format
     - -f
     - Sets the output format for the read, reference and highlight data
     - json
   * - aux_tag
     - -x
     - Displays the given content of the aux tag in the tooltip of the plot. Multiple usage for more than one tag is possible.
     -
   * - spec-output
     -
     - If present vega-lite specs will be written to the given file path
     -
   * - read-data-output
     -
     - If present read data will be written to the given file path
     -
   * - ref-data-output
     -
     - If present reference data will be written to the given file path
     -
   * - highlight-data-output
     -
     - If present highlight data will be written to the given file path
     -
   * - html
     -
     - If present the generated plot will inserted into a plain html file containing the plot centered which is then written to stdout
     -
   * - no-embed-js
     -
     - If present, the generated html will not embed javscript dependencies and therefore be considerably smaller but require internet access to load the dependencies.
     - false
   * - around-vcf-record
     -
     - Plots a region around a specified VCF record taken via its index from the VCF file given via the --vcf option.
     - 

