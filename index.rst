:tocdepth: 1

.. sectnum::

.. Metadata such as the title, authors, and description are set in metadata.yaml

.. TODO: Delete the note below before merging new content to the main branch.

.. note::

   **This technote is a work-in-progress.**

Abstract
========

This document describes the concept of operations for running the Auxiliary Telescope in Survey Mode, which will become the primary operational mode for AuxTel. 
The Survey Mode utilizes semi-autonomous, scheduler-driven operations and the roles, responsibilities, and expectations for this mode are defined. 

Guidelines for Operations
=========================

Survey mode is intended to be the primary mode for Auxiliary Telescope (AuxTel) operations. 
It is a passive mode of operations, with nighttime observations driven by the Scheduler with minimal staff intervention. 
The central tenant of operations in this mode is that the AuxTel operations are secondary to any responsibilities the summit staff may have related to Simonyi Survey Telescope operations. 

This results in the following guidelines for operations in survey mode: 

- The observing staff are not be required to actively monitor or report on incoming data quality.
- Logging will be minimal; limited to short narrative statements needed to report on changes during the night or provide context for faults and recovery attempts.
- Faults will be recovered when observing staff have available time, and the AuxTel may remain in Standby state during the night for extended periods of time. 
- Remote support will be available for fault resolution on an on-call basis. 
- Any faults which put hardware at risk will be result in closing the AuxTel early for the night.
- The decision for closing the AuxTel early is to be made by observing staff on summit, no additional approval is required.

Daytime activities
==================

Daytime Checkouts
-----------------
Daytime checkouts should be run once per week, preferable on Monday afternoons. 
They should also be run following any major software updates (such as a new cycle release), or hardware changes and fault recoveries.
They can be performed any time during the day when the system is available. 

Afternoon Calibrations and Venting
----------------------------------
Afternoon calibrations and venting, including opening the vent gates and enabling the fan, will be performed daily by the daytime observing specialist on a best-effort basis. 
That is to say, if daytime engineering work within AuxTel prevents us from starting calibrations and venting before 16:00, these tasks can be skipped at the discretion of the daytime observing specialist.

Nighttime Activities
====================

Nighttime Operations
--------------------
The AuxTel should be entirely scheduler-driven at night while in survey mode. 
A single scheduler configuration should be provided each night to prevent detailed night plans requiring active observing support.
Once the daytime activities are complete, the telescope can be prepare for on-sky observations and the scheduler configured at any time before twilight. 
The AuxTel should continue to be run during the night until the observing team on the summit deems it necessary to close.

Fault resolution
----------------
Faults which interrupt observations in this mode shall be recovered when the observing specialists on the summit have time and are not occupied by responsibilities related to Simonyi Survey Telescope operations. 
When faults occur which result only in script failures that do not result in hardware risk or CSC components going into fault state, operations should be recovered by simply playing the script queue. 
The scheduler and standard scripts used during observations are required to be robust against such failure, and should not leave the system in an inoperable state in the case of script failure alone.
Faults that result in CSC components going into fault state and which require intervention from the observing specialists to recover will be recovered when possible. 
CSC faults may result in the system remaining inoperable for extended periods of time if the observing specialists are unavailable to recover. 
In this case, the CSCs in fault should be transitioned to Standby while they await availability to resolve to prevent warning messages being broadcast. 
Remote support can be utilized to recover the system with explicit approval from the observing specialists on shift. 

Roles and Responsibilities
==========================

Daytime Observing Specialist Shift
----------------------------------
The Daytime Shift is expected to attend the 09:30 morning meeting and report on any known failures that require daytime resources.
They are also expected to follow any on-going work during the day. 
They are responsible for deciding if/when it is appropriate to start daytime calibrations and venting. 
If Simonyi Survey telescope responsibilities prevent the Daytime Shift from completing calibrations and venting, they may be skipped. 

Flex/Nighttime Observing Specialist Shift
-----------------------------------------
The Nighttime Shift is responsible for passively monitoring AuxTel status throughout the night. 
This does not include monitoring data quality, but only operational status. 
If a fault is encountered throughout the night, it should be recovered when appropriate. 
At the end of the night, the telescope should be shutdown using a standard set of procedures. 

Remote Support
--------------
During operation of AuxTel in survey mode, remote support is expected to be available on-call in case of risk to the hardware.
Fault resolution should be handled by the observing specialist on shift, 
and if the fault cannot be recovered and remote support is not available, 
it is acceptable for the observing specialist to shut down the AuxTel early to avoid distraction from responsibilities related to the Simonyi Survey Telescope. 

Example 24hr timeline
=====================
Below is an example 24hr timeline of AuxTel operations in survey mode. 
All times are given in local (Chile) time. 

- *09:30* : Summit coordination meeting, attended by member of SITCOM and Daytime Observing Specialist. Any issues from prior night are discussed and resources allocated to AuxTel daytime work if needed.
- *15:00* : Progress on AuxTel Dome daytime work is assessed by Daytime Observing Specialist. Readiness for daytime checkouts, venting, and calibrations is determined. If it is determined we are unable to proceed with daytime checkouts, calibrations and/or venting, they may be skipped entirely.
- *16:00* : Afternoon checkout, calibrations, and/or venting scripts are queued up by Daytime Specialist. AuxTel dome is prepared for venting. 
- *17:30* : Start of night scripts (prepare_for_onsky, enable scheduler, resume scheduler) are queued up by Daytime Specialist. These can be added directly to the queue at any time following daytime activities, including before heading down for dinner.
- *18:30 to 06:00* : AuxTel is operated in scheduler-driven mode, with passive monitoring by on-shift specialist. Control of AuxTel is handed over to Flex/Nighttime Observing Specialist at shift change boundary.

.. Make in-text citations with: :cite:`bibkey`.
.. Uncomment to use citations
.. .. rubric:: References
.. 
.. .. bibliography:: local.bib lsstbib/books.bib lsstbib/lsst.bib lsstbib/lsst-dm.bib lsstbib/refs.bib lsstbib/refs_ads.bib
..    :style: lsst_aa
