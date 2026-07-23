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
     - BAM file(s) to be visualized. Multiple files can be given (e.g. ``-b a.bam -b b.bam``) and will be stacked in the resulting plot.
     -
   * - reference
     - -r
     - The path to the reference fasta file
     -
   * - region
     - -g
     - Chromosome and region (1-based, fully inclusive) for the visualization. Example: 2:132424-132924
     -
   * - around
     - -a
     - A chromosome and a base position that will define the region that will be plotted starting 500bp before and end 500bp after the given position. Example: 2:20000
     -
   * - highlight
     - -h
     - Named intervals or single base positions that will be highlighted in the visualization. Example: myinterval:132400-132500 or myvariant:132440
     -
   * - vcf
     - -v
     - Path to a VCF file that will be used to highlight all variant positions located within the given region.
     -
   * - bed
     -
     - Path to a BED file that will be used to highlight all BED records overlapping the given region.
     -
   * - plot-all
     -
     - Plot the whole bam file(s) (no ``-g``/``-a`` needed). We advise to only use this option for small bam files, and it cannot be combined with multiple bam files that have different targets.
     - false
   * - max-read-depth
     - -d
     - Set the maximum rows of reads that will be shown in the alignment plots
     - 500
   * - max-width
     - -w
     - Set the maximum width of the resulting alignment plot. Defaults to 1024, or to the available width when rendering to HTML.
     - 1024
   * - output
     - -o
     - If present, data and vega-lite specs of the generated plot will be split and written to the given directory. Cannot be combined with any of the ``*-output`` options, ``--html`` or ``--no-embed-js``.
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
   * - coverage-output
     -
     - If present coverage data will be written to the given file path
     -
   * - highlight-data-output
     -
     - If present highlight data will be written to the given file path. Requires ``--highlight`` to be set.
     -
   * - html
     -
     - If present the generated plot will inserted into a plain html file containing the plot centered which is then written to stdout
     -
   * - no-embed-js
     -
     - If present, the generated html will not embed javascript dependencies and therefore be considerably smaller but require internet access to load the dependencies.
     - false
   * - around-vcf-record
     -
     - Plots a region around a specified VCF record taken via its index (starting at 0) from the VCF file given via the ``--vcf`` option. Requires ``--vcf`` and cannot be combined with ``--region``, ``--around`` or ``--plot-all``.
     -
   * - mismatch-display-min-percent
     -
     - The generated coverage plot will only display mismatches with a minimum percentage of the total read depth.
     - 1.0
   * - clamp-reads
     -
     - If set, reads are clamped to the boundaries of the specified region before processing.
     - false

