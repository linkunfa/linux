.. SPDX-License-Identifier: GPL-2.0

.. include:: <isonum.txt>

NPCM video driver
=================

This driver is used to control the Video Capture/Differentiation (VCD) engine
and Encoding Compression Engine (ECE) present on Nuvoton NPCM SoCs. The VCD can
capture and differentiate video data from digital or analog sources, then the
ECE will compress the data into HEXTILE format.

Driver-specific Controls
------------------------

V4L2_CID_NPCM_CAPTURE_MODE
~~~~~~~~~~~~~~~~~~~~~~~~~~

The VCD engine supports two modes:

- COMPLETE mode:

  Capture the next complete frame into memory.

- DIFF mode:

  Compare the incoming frame with the frame stored in memory, and updates the
  differentiated frame in memory.

Application can use ``V4L2_CID_NPCM_CAPTURE_MODE`` control to set the VCD mode
with different control values:

- ``V4L2_NPCM_CAPTURE_MODE_COMPLETE``: set to COMPLETE mode.
- ``V4L2_NPCM_CAPTURE_MODE_DIFF``: set to DIFF mode.

V4L2_CID_NPCM_RECT_COUNT
~~~~~~~~~~~~~~~~~~~~~~~~

The ECE will compress the captured data into HEXTILE format. Application can use
``V4L2_CID_NPCM_RECT_COUNT`` control to get the count of compressed HEXTILE
rectangles which is relevant to the number of differentiated frames if VCD is in
DIFF mode. And the count will always be 1 if VCD is in COMPLETE mode.

References
----------
include/uapi/linux/npcm-video.h

**Copyright** |copy| 2022 Nuvoton Technologies
