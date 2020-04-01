# DHUS Addon - ERS-1/2 Mission

The datasets are split by these two missions:

* ERS-1
* ERS-2

Links - User manuals, information sheets, guides: 
* https://earth.esa.int/documents/10174/1598482/GEN02C.pdf
* https://earth.esa.int/c/document_library/get_file?folderId=13019&name=DLFE-570.pdf
* https://directory.eoportal.org/web/eoportal/satellite-missions/e/ers-1
* https://directory.eoportal.org/web/eoportal/satellite-missions/e/ers-2
* https://earth.esa.int/documents/10174/437508/ATSR-L1B-and-L2-Products-Envisat-Format-Rel-3-0.pdf
## ATSR Instrument

The metadata between AR and TOA datasets seems to be the same.

### AR Datasets

First ~234 lines of the AR datasets are metadata fields. Most of the metadata fields are references and byte locations to non existing `.ast` and other files. The first ~72 lines should contain relevant metadata that can be extracted.

Each dataset is made up of 3 files

* A non gdal recognized ENVISAT FORMAT image that contains
    * A readable plaintext header
    * Binary image
* `.log` file
* `.md5` checksum file

### TOA Datasets

First ~365 lines of the TOA datasets are metadata fields. Most of the metadata fields are references and byte locations to non existing `.ast` and other files. The first ~75 lines should contain relevant metadata that can be extracted.

Each dataset is made up of 4 files

* The non gdal recognized ENVISAT FORMAT image that contains
    * Readable plaintext header
    * Binary image 
* `.log` file
* `.md5` checksum file
* `.OT` with some decimals/paths/logs

## WS Instrument
