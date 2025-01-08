.. Soft-Tester UE documentation master file, created by
   sphinx-quickstart on Thu Sep 12 16:04:18 2024.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

NTIA Software Tester UE
==========================

Penetration testing tool for Software Defined Radio

Overview
--------

This project is a security testing tool based on srsRAN Project's User Equipment, used to test 5G and open radio access networks (RANs) via the Uu air interface between the UE and the network. While this enables different types of testing, the focus of the software is on RAN security testing. This soft T-UE is fully software-defined and compatible with widely available, commercial off-the-shelf software radio hardware. Standardized 3GPP or O-RAN tests as well as custom test procedures can then be implemented and executed at minimal cost and at different stages of RAN development and integration. This system allows for testing many commercial and open source random access networks with minimal technical overhead. Many attacks on the RAN can be run automatically by the system.


System Architecture
--------------------

.. image:: images/placeholder.png

.. toctree::
   :maxdepth: 1
   :caption: General

   Installation guide <rstFiles/installation>
   Components of Soft-T UE <rstFiles/components>
   
.. toctree::
   :maxdepth: 1
   :caption: Attacks implemented

   attacks/jamming_attack.rst
  