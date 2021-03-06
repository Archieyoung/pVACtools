.. image:: ../images/pVACseq_logo_trans-bg_sm_v4b.png
    :align: right
    :alt: pVACseq logo

Getting Started
---------------

pVACseq provides a set of example data to show the expected input and output files. You can download the data set by running the ``pvacseq download_example_data`` :ref:`command <example_data>`.

The example data output can be reproduced by running the following command:

.. code-block:: none

   pvacseq run \
   <example_data_dir>/input.vcf \
   Test \
   HLA-A*02:01,HLA-B*35:01,DRB1*11:01 \
   MHCflurry MHCnuggetsI MHCnuggetsII NNalign NetMHC PickPocket SMM SMMPMBEC SMMalign \
   <output_dir> \
   -e 8,9,10

A detailed description of all command options can be found on the :ref:`Usage <pvacseq_run>` page.

.. _pvacseq_docker:

Running pVACseq using Docker
____________________________

A pVACtools Docker image is available on `DockerHub <https://hub.docker.com/r/griffithlab/pvactools>`_ using the
``griffitlab/pvactools`` tag. After `installing Docker <https://docs.docker.com/install/>`_
you can start an interactive Docker instance by running the following command:

.. code-block:: none

   docker run -it griffithlab/pvactools

Version-specific images are available and can be run like so:

.. code-block:: none

   docker run -it griffithlab/pvactools:<version>

In order to have access to your local data inside of the Docker container you
will need to mount a local volume inside of the container. This is done using
the ``-v`` flag. For example, you can mount your
``/local/path/to/example_data_dir`` in your container like so:

.. code-block:: none

   docker run -v /local/path/to/example_data_dir:/pvactools_example_data -it griffithlab/pvactools

This will mount the ``example_data_dir`` inside the container as the
``/pvacseq_example_data`` directory. When you are inside of the container
you will now have access to all of the data that was inside of the
``example_data_dir`` from the ``/pvaseq_example_data`` directory.

You will need to do the same thing for your ``/local/path/to/output_dir`` so that any output
written by pVACseq will be accessible from your machine outside of your Docker
container.

.. code-block:: none

   docker run -v /local/path/to/example_data_dir:/pvacseq_example_data -v /local/path/to/output_dir:/pvacseq_output_data -it griffithlab/pvactools

You can now run your pVACseq command like so:

.. code-block:: none

   pvacseq run \
   /pvacseq_example_data/input.vcf \
   Test \
   HLA-A*02:01,HLA-B*35:01,DRB1*11:01 \
   MHCflurry MHCnuggetsI MHCnuggetsII NNalign NetMHC PickPocket SMM SMMPMBEC SMMalign \
   /pvacseq_output_data \
   -e 8,9,10
   --iedb-install-directory /opt/iedb

The output from your pVACseq run can be found under ``/pvacseq_output_data``
inside of the container and ``/local/path/to/output_dir`` on your local
machine.

Please note that our Docker container already includes installations of the IEDB class I and class II tools at ``/opt/iedb`` (``--iedb-install-directory /opt/iedb``).
