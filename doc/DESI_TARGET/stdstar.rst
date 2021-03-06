===============
stdstar-\*.fits
===============

General Description
===================

Summary
-------

DESI Stdstar files contain a single binary table covering the entire footprint.  
They contain the positions of standard stars that must be targeted for calibration.

Naming Convention
-----------------

TBD, let's try ``stdstar-{version}.fits`` where ``version`` is the code version
that wrote this, preferably a git tag of desitargets.

regex: ``stdstar-v?[0-9]+\.[0-9]+(\.[0-9]+|)\.fits``

Contents
========

====== ======= ======== ===================
Number EXTNAME Type     Contents
====== ======= ======== ===================
HDU0_          IMAGE    Blank
HDU1_  STDSTAR BINTABLE Standard Star table
====== ======= ======== ===================


FITS Header Units
=================

HDU0
----

Empty header.

HDU1
----

STDSTAR.

Required Header Keywords
~~~~~~~~~~~~~~~~~~~~~~~~

======== ======================================================== ==== ===================================
KEY      Example Value                                            Type Comment
======== ======================================================== ==== ===================================
EXTNAME  STDSTAR                                                  str  name of this binary table extension
DEPNAM00 desitarget                                               str
DEPVER00 0.1.0                                                    str  desitarget.__version__
DEPNAM01 desitarget-git                                           str
DEPVAL01 0.1.0                                                    str  git revision
DEPNAM02 tractor-files                                            str
DEPVER02 /project/projectdirs/cosmo/data/legacysurvey/dr1/tractor str  input directory
======== ======================================================== ==== ===================================

Required Data Table Columns
~~~~~~~~~~~~~~~~~~~~~~~~~~~

===================== ========== ===== ===================
Name                  Type       Units Description
===================== ========== ===== ===================
TARGETID              int64            ID (unique to file and the whole survey)
RA                    float64          Right ascension [degrees]
DEC                   float64          Declination [degrees]
DESI_TARGET           int64            DESI (dark time program) target selection bitmask
BGS_TARGET            int64            BGS (bright time program) target selection bitmask
MWS_TARGET            int64            MWS (bright time program) target selection bitmask
===================== ========== ===== ===================


Notes and Examples
==================

In general, the above format contains:

* Columns needed for traceability (e.g. TARGETID, DESI_TARGET, BGS_TARGET, MWS_TARGET)
* Columns needed by fiber assignment (e.g. RA, DEC)

TARGETID, DESI_TARGET, BGS_TARGET and MWS_TARGET are created by target selection; the rest are pass through from the original input tractor files

See http://legacysurvey.org for more details about the columns from input tractor files
