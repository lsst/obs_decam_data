# obs_decam_data
Repository to hold data related to the obs_decam package.

## Defects
These defects were written using files retrieved on 16 May 2019 from: ftp://ftp.noao.edu/pub/valdes/DECamCPCalFiles150123/
The files are:
* `DECamMasterCal_56475-bpm.tgz`
* `DECamMasterCal_56876-bpm.tgz`

These tarballs contain one file per sensor in the focalplane.
Each file has an ISO compliant timestamp in the filename.
The timestamp is taken to be the `valid_start` time.

These masks are turned in to LSST style mask images with the single `BAD` bad bit set.
Any non-zero pixel in the BPM was assigned the `BAD` flag.
We construct `meas_algorithms.Defects` from the mask.
We update metadata and write the file back out to the appropriate path determined from the sensor number and time stamp.
