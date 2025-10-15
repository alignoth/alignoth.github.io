.. _embedding:

**************************
Embedding Alignoth Outputs
**************************

Alignoth produces fully self-contained HTML files that can be easily embedded into other reports and workflows.
This allows users to integrate alignment visualizations directly into existing analysis pipelines, documentation,
or automated reporting systems such as Snakemake or Datavzrd.

Below we demonstrate how to embed Alignoth visualizations within a Snakemake report.  
Additional examples for Datavzrd and other tools will be added in future updates.

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
      - alignoth=0.16.4

After your regular workflow execution the snakemake report can be generated via the following command:

.. code-block:: bash

    snakemake --report report.zip

The resulting report will contain the interactive Alignoth plot.

