# `obs_decam_data`
Repository to hold data related to the `obs_decam` package.

## Defects
These defects were written using files accessed from `lsst_dev` on 11 June 2019 from: `/datasets/decam/_internal/calib/bpmDes/`.

These directories contain one file per sensor in the focalplane.
Each file has an ISO compliant timestamp in the filename.
The timestamp is taken to be the `valid_start` time.

These masks are turned in to LSST style mask images with the single `BAD` bad bit set.
Any non-zero pixel in the BPM was assigned the `BAD` flag.
We construct `meas_algorithms.Defects` from the mask.
We update metadata and write the file back out to the appropriate path determined from the sensor number and time stamp.

## Crosstalk
The crosstalk terms contained here are the results processed from `obs_decam/decam/DECam_xtalk_20130606.txt` (7 May 2020; using github master) using the `obs_decam` `makeCrosstalkDecam.py` script.  The directory structure and filenames match what is done with the defects above.  These yaml files can be used to construct `lsst.ip.isr.CrosstalkCalib` python objects using that class's `readText` method.  Both intra- and inter- chip crosstalk terms are listed in the objects.
