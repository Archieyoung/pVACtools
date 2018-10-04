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
   MHCflurry MHCnuggetsI MHCnuggetsII NNalign NetMHC PickPocket SMM SMMPMBEC SMMalign
   <output_dir> \
   -e 8,9,10

A detailed description of all command options can be found on the :ref:`Usage <pvacseq_run>` page.
