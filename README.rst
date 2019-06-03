=================
Library Simulator
=================

Library simulator is a python package for generating random mutagenesis
libraries given a nucleotide sequence and error-prone polymerase. 

Examples
========

.. code:: python
    from library_simulator import LibrarySimulator
    lib = LibrarySimulator("example.fasta",mutation_spectrum="published")
    lib.simulate(num_samples=10,mutation_rate=2)
    lib.clones

.. image:: example/output-table.png

See :code:`example/examples.ipynb` for more functionality.

Key
---
- **aa**: amino acid changes (:code:`*`: new stop codon)
- **base**: base changes (:code:`-` and :code:`+` are insertions and deletions)
- **num**: total number of amino acid changes (could be a huge number if there is
  an early stop or indel)
- **indel**: whether or not there is an indel
- **stop**: whether or not there is new stop codon
- **start**: whether or not the real start codon was messed up

Installation
============

.. code:: python
    pip install library_simulator


Assumptions
===========

- The number of mutations per clone is determined by a Poisson process.
- The sites mutated are independent within a clone and between clones
- The probability of each possible mutation (A->T, G->C, etc.) is determined
  by the enzyme, not the sequence.  The profiles for different enzymes
  are found in: :code:`library_simulator/mutation_spectra`