# DHUS Addon - ERS-1/2 Mission

References: 
* https://directory.eoportal.org/web/eoportal/satellite-missions/e/ers-1
* https://directory.eoportal.org/web/eoportal/satellite-missions/e/ers-2

The datasets are split by these two missions.

## ATSR Instrument

### AR Datasets

First 234 lines of the AR datasets are metadata fields

Each dataset is made up of 3 files

* A non gdal recognized image that contains
    * A readable plaintext header
    * Binary image
* `.log` file
* `.md5` checksum file

### TOA Datasets

First 365 lines of the TOA datasets are metadata fields

Each dataset is made up of 4 files

* The non gdal recognized image that contains
    * Readable plaintext header
    * Binary image
* `.log` file
* `.md5` checksum file
* `.OT` with some decimals/paths/logs

## WS Instrument