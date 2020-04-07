# DHUS Addon - ERS-1/2 Mission

The datasets are split in two missions:

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

The naming scheme of datasets is:

AT1_AR__2PURALYYYYMMDD_HHMMSS_< sequence of digits>_<5 digits relative orbit>_<5 digits absolute orbit>_< sequence of digits>

Each dataset is made up of 3 files

* A non gdal recognized ENVISAT FORMAT image that contains
    * A plaintext header
    * Binary image
* `.log` file
* `.md5` checksum file

A metadata sample is in `metadata_sample_ar`.

### TOA Datasets

First ~365 lines of the TOA datasets are metadata fields. Most of the metadata fields are references and byte locations to non existing `.ast` and other files. The first ~75 lines should contain relevant metadata that can be extracted.

The naming scheme of datasets is:

AT1_TOA_1PURALYYYYMMDD_HHMMSS_< sequence of digits>_<5 digits relative orbit>_<5 digits absolute orbit>_< sequence of digits>

Each dataset is made up of 4 files

* The non gdal recognized ENVISAT FORMAT image that contains
    * A plaintext header
    * Binary image 
* `.log` file
* `.md5` checksum file
* `.OT` with some decimals/paths/logs

A metadata sample is in `metadata_sample_toa`.

## WS Instrument

The datasets are split into two series:
* ASPS20.H
* ASPS20.N

The naming scheme of datasets is:

ASPS20_<H|N>_YYMMDDHHMMSS

Each dataset is a NetCDF file with metadata as attributes. Additionally, there is a `.md5` checksum file. The datasets show CF-1.6 as a standard, but a compliance checker points out some errors:
 * https://git.eodc.eu/datahubrelay/dhus-ers-1-2/snippets/8

Both series share the same set of metadata.

A sample of metadata is in `metadata_sample_ws.json`.