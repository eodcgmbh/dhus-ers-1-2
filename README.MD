# DHUS Addon - ERS-1/2 Mission

References: 
* https://directory.eoportal.org/web/eoportal/satellite-missions/e/ers-1
* https://directory.eoportal.org/web/eoportal/satellite-missions/e/ers-2

The datasets are split by these two missions:

* ERS-1
* ERS-2

## ATSR Instrument

The metadata between AR and TOA datasets seems to be the same.

### AR Datasets

First ~234 lines of the AR datasets are metadata fields. Most of the metadata fields are references and byte locations to non existing `.ast` and other files. The first ~72 lines should contain relevant metadata that can be extracted.

Each dataset is made up of 3 files

* A non gdal recognized image that contains
    * A readable plaintext header
    * Binary image
* `.log` file
* `.md5` checksum file

### TOA Datasets

First ~365 lines of the TOA datasets are metadata fields. Most of the metadata fields are references and byte locations to non existing `.ast` and other files. The first ~75 lines should contain relevant metadata that can be extracted.

Each dataset is made up of 4 files

* The non gdal recognized image that contains
    * Readable plaintext header
    * Binary image
* `.log` file
* `.md5` checksum file
* `.OT` with some decimals/paths/logs

## WS Instrument