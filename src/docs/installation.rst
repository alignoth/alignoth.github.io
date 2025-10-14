******************
Installation Guide
******************

There are multiple ways to install alignoth:

Pixi
~~~~
Alignoth can be easily installed globally using `pixi <https://pixi.sh/>`_:

.. code-block:: bash

    pixi global install alignoth

Bioconda
~~~~~~~~
Alignoth is available via `Bioconda <https://bioconda.github.io>`_.
With Bioconda set up, installation is as easy as:

.. code-block:: bash

    conda install alignoth -c conda-forge -c bioconda -c nodefaults

Pay attention to the correct channel ordering for the installation.

Cargo
~~~~~
If the `Rust <https://www.rust-lang.org/tools/install>`_ compiler and associated `Cargo <https://github.com/rust-lang/cargo/>`_ are installed, alignoth may be installed via:

.. code-block:: bash

    cargo install alignoth

Docker
~~~~~~
Alignoth is also available as a prebuilt container through `Biocontainers <https://biocontainers.pro/tools/alignoth>`_.  
This image provides a ready-to-use environment with all dependencies preinstalled, making it convenient for users who prefer containerized workflows or encounter issues with native installations.

To pull and run the image directly from Quay.io, use:

.. code-block:: bash

    docker pull quay.io/biocontainers/alignoth:<version>
    docker run --rm quay.io/biocontainers/alignoth:<version> alignoth --help

Replace ``<version>`` with the desired release tag (e.g., ``0.16.4--h1520f10_0``).  
A list of all available versions can also be found on the `Biocontainers page <https://biocontainers.pro/tools/alignoth>`_.


Source
~~~~~~
Download the source code and within the root directory of source run:

.. code-block:: bash

    cargo install
