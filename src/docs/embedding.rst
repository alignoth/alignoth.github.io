.. _embedding:

**************************
Embedding Alignoth Outputs
**************************

Alignoth produces fully self-contained HTML files or Vega-Lite plots that can be easily embedded into other reports and workflows.
This allows users to integrate alignment visualizations directly into existing analysis pipelines or tools such as Snakemake or Datavzrd.

Below we demonstrate how to embed Alignoth visualizations within a Datavzrd and Snakemake report.  

Embedding in Datavzrd
=====================

`Datavzrd <https://datavzrd.github.io>`_ allows embedding Vega-Lite plots via its `render-plot` keyword.
This enables embedding one or more Alignoth plots directly into a Datavzrd report.
These views (e.g. per variant or gene of interest) can be linked to an overview table via Datavzrd's `linking feature <https://datavzrd.github.io/docs/configuration.html#links>`_.
Technically embedding the alignment views can be achieved by calling Alignoth asking for a tsv formatted output using ``-f tsv`` and an output directory ``-o output/`` for the datasets and Vega-Lite spec files like this:

.. code-block:: bash

    alignoth -b sample.bam -g chr1:1000-1500 -r reference.fa -o output/ -f tsv

This command will create the following directory structure:

.. code-block:: bash

    output/
    ├── sample.coverage.tsv
    ├── sample.reads.tsv
    ├── sample.reference.tsv
    ├── sample.vl.json

Next, a minimal Datavzrd configuration for embedding an Alignoth view looks like this:

.. code-block:: yaml

    datasets:
      sample.coverage:
        path: output/sample.coverage.tsv
        separator: "\t"
      sample.reference:
        path: output/sample.reference.tsv
        separator: "\t"
      sample.reads:
        path: output/sample.reads.tsv
        separator: "\t"
    views:
      sample:
          datasets:
              reads: sample.reads
              reference: sample.reference
              coverage: sample.coverage
          render-plot:
              spec-path: "output/sample.vl.json"


Embedding in Snakemake
======================

Snakemake can generate detailed, self-contained HTML reports that include any desired output file produced by the workflow.  
By wrapping an Alignoth HTML output in the ``report()`` function, it will be automatically integrated into the resulting Snakemake report.

Example rule
------------

.. code-block:: python

    rule alignoth:
        input:
            bam="results/mapped/{sample}.bam",
            bam_index="results/mapped/{sample}.bam.bai",
            ref="results/ref.fasta"
        output:
            report("results/alignoth/{sample}/pileup.html")
        log:
            "logs/alignoth/{sample}.log"
        conda:
            "envs/alignoth.yaml"
        shell:
            """
            alignoth -b {input.bam} -r {input.ref} -g chr1:1-1000 --html > {output} 2> {log}
            """

The corresponding Conda environment definition:

.. code-block:: yaml

    name: alignoth
    channels:
      - conda-forge
      - bioconda
    dependencies:
      - alignoth=1.3.0

After your regular workflow execution the snakemake report can be generated via the following command:

.. code-block:: bash

    snakemake --report report.zip

The resulting report will contain the interactive Alignoth plot.

