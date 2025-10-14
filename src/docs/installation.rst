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

Bioconatiners also offer `ready-to-pull containers <https://biocontainers.pro/tools/alignoth>` with alignoth already installed. 

Source
~~~~~~
Download the source code and within the root directory of source run:

.. code-block:: bash

    cargo install
