===========================
qa-getrms-CAMERA-EXPID.yaml
===========================

:Summary: This QA for QuickLook includes the calculation of the RMS
        of pixel values in the 2-D pix file after the preprocessing stage. 
:Naming Convention: ``qa-getrms-{ARM}{SPECTROGRAPH}-{EXPID}.yaml``, where 
        {ARM} is the 1-char arm name (r,b,z), {SPECTROGRAPH} indexes 
        CCDs 0-9 on that arm, and {EXPID} is the 8-digit exposure ID.  
        Together, {ARM}{SPECTROGRAPH} specify a {CAMERA}.
:Regex: ``qa-getrms-[brz][0-9]-[0-9]{8}\.yaml``
:File Type:  YAML


Inputs
======

Written by qa_quicklook.py, with Get_RMS using:

- pix 2D file

Contents
========

========== ================ ===========================
KEYNAME    Type             Contents
========== ================ ===========================
GETRMS     Py dictionary    image root-mean-squared
========== ================ ===========================



Dictionary Contents
===================

KEYNAME = GETRMS

Spectral root-mean-squared calculations per image and per CCD amp.

Keyword Description
~~~~~~~~~~~~~~~~~~~

================ ============= ========== ==============================================
KEY              Example Value Type       Comment
================ ============= ========== ==============================================
ARM              r             char       Spectrograph arm b,r,z
SPECTROGRAPH     0             int  	  Camera index 0..9
EXPID            00000002      int  	  exposure ID
QANAME		 GETRMS        string     name of QA algorithm
PANAME           PREPROC       string     name of pipeline algorihm
TIMESTAMP        12.01234      float      time in hours of the day (UTC) of QA execution
RMS              10.0          float      value of RMS across image
RMS_AMP          9.12          float[4]   value of RMS averagedover each amplifier
================ ============= ========== ==============================================

Example YAML Output
~~~~~~~~~~~~~~~~~~~

::

    {'GETRMS': 
        {'EXPID': '00000002', 'SPECTROGRAPH': 0, 'ARM': 'r', 'PANAME': 'PREPROC', 'TIMESTAMP', 12.0123, 
         'VALUE': 
             {'RMS': 10.0,
	      'RMS_AMP': array([9.12, 10.88, 0., 0. ])
	     }
         }
     }
