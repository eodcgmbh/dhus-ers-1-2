# The DHuS Addon for ERS-1/2

## Introduction.

The DHuS addon is a Java package that contains the definitions and extraction rules and operations for the Envisat products. The central element of this package is the ontology definition file ([aeolus.owl](src/main/resources/META-INF/ers12.owl)) located in the META-INF folder inside the resources directory.

The addon works in conjunction with the DRBX cortex definition (separate package), currently designed to support the following product types from the Envisat satellite mission:

- ASPS products (AMI sensor)
  - ASPS20.H
  - ASPS20.N
- ATSR sensor
  - AT1\_AR\_\_2P
  - AT1\_NR\_\_2P
  - AT1\_TOA\_1P
  - AT2\_AR\_\_2P
  - AT2\_TOA\_1P
  - AT2\_NR\_\_2P
- RA sensor
  - ERS\_ALT\_2\_
  - ERS\_ALT\_2M
  - ERS\_ALT\_2S

## Metadata Attributes

All metadata that will be extracted and made available via DHuS is defined within the OWL file mentioned above. The following is a complete list of metadata attributes implemented with this addon. Sample outputs to demonstrate which values these attributes can take can be found in the [samples](src/main/resources/samples) folder inside the resources directory.

| OData Name                 | OpenSearch Name          | Description                                                                          | ASPS    | ATSR    | RA      |
|----------------------------|--------------------------|--------------------------------------------------------------------------------------|---------|---------|---------|
| Satellite                  | -                        | Name of the satellite                                                                | &#9745; | &#9745; | &#9745; |
| Instrument                 | -                        | Name of the instrument                                                               | &#9745; | &#9745; | &#9745; |
| Date                       | -                        | Same as sensing start date                                                           | &#9745; | &#9745; | &#9745; |
| Sensing start              | beginposition            | Sensing start date                                                                   | &#9745; | &#9745; | &#9745; |
| Sensing stop               | endposition              | Sensing stop date                                                                    | &#9745; | &#9745; | &#9745; |
| Footprint                  | gmlfootprint             | GML footprint                                                                        | &#9745; | &#9745; | &#9745; |
| JTS footprint              | footprint                | JTS footprint                                                                        | &#9745; | &#9745; | &#9745; |
| Platform name              | platformname             | Name of the platform                                                                 | &#9745; | &#9745; | &#9745; |
| Platform short name        | platformshortname        | Short name of the platform                                                           | &#9745; | &#9745; | &#9745; |
| Platform serial identifier | platformserialidentifier | Identification number of the platform among the mission                              | &#9745; | &#9745; | &#9745; |
| Platform NSSDC identifier  | platformnssdcidentifier  | The National Space Science Data Center (NSSDC) identification number of the platform | &#9745; | &#9745; | &#9745; |
| Instrument name            | instrumentname           | Name of the instrument                                                               | &#9745; | &#9745; | &#9745; |
| Instrument short name      | instrumentshortname      | Short name of the instrument                                                         | &#9745; | &#9745; | &#9745; |
| Orbit number               | orbitnumber              | Absolute orbit number                                                                | &#9745; | &#9745; | &#9745; |
| Relative orbit number      | relativeorbitnumber      | Relative orbit number                                                                | &#9744; | &#9745; | &#9745; |
| Cycle                      | cycle                    | Number of cycles                                                                     | &#9744; | &#9745; | &#9745; |
| Phase                      | phase                    | Mission phase                                                                        | &#9744; | &#9745; | &#9744; |
| Processing level           | processinglevel          | The value of the last processing                                                     | &#9745; | &#9745; | &#9745; |
| Processing center          | processingcenter         | Processing center ID                                                                 | &#9745; | &#9744; | &#9745; |
| Generation time            | -                        | Product generation date                                                              | &#9745; | &#9744; | &#9745; |
| Product type               | producttype              | Product type designation                                                             | &#9745; | &#9745; | &#9745; |
| Product description        | productdescription       | One line description of the file                                                     | &#9745; | &#9744; | &#9745; |
| Size                       | size                     | File size                                                                            | &#9745; | &#9745; | &#9745; |
| Format                     | format                   | Product format description                                                           | &#9745; | &#9745; | &#9745; |
| Filename                   | filename                 | File name                                                                            | &#9745; | &#9745; | &#9745; |


More information on the source of the respective attributes can be found directly by looking at the OWL file itself.

## Footprint Extraction

The footprint coordinates are extracted from the mixed ASCII/binary data file (E1/E2) or the netCDF (nc) fil, depending on the product. For the E1/E2 files, the cortex topic (separate package) uses an XML schema definition file to create a tree of nodes which is then navigable within the addon OWL. This functionality is already provided for netCDF files by using the DRB netCDF extension in the topic class definition.

### Latitudes and Longitudes

The generation of the footprints is based on the following sources:

- ASPS: Latitude (lat) and Longitude (lon) variables in netCDF (Table 9 in [ASPS Product Format](https://earth.esa.int/documents/700255/1743979/ERSE-GSEV-EOPG-RS-06-0002_ver2.5_ASPS_Product_Format.pdf/b58b6e60-e0b4-4adc-9dca-685c00f0c5e3))
- ATSR AR: Latitude and Longitude of the SST Record 30 arc minute cell MDS (Section 7.5.3.8.4 in [ENVISAT-1 PRODUCTS SPECIFICATIONS, VOLUME 7: AATSR PRODUCTS SPECIFICATIONS](https://earth.esa.int/documents/700255/2042507/Vol-07-Aats-4C.pdf/71cd7964-7860-4df7-abe5-5042b76cc31f))
- ATSR NR and TOA: Tie point latitudes and longitudes (Table 7.4.1.7.2-1 in [ENVISAT-1 PRODUCTS SPECIFICATIONS, VOLUME 7: AATSR PRODUCTS SPECIFICATIONS](https://earth.esa.int/documents/700255/2042507/Vol-07-Aats-4C.pdf/71cd7964-7860-4df7-abe5-5042b76cc31f))
- RA: Latitude (lat) and Longitude (lon) variables in netCDF (Section 5.3.4 and 5.3.5 in [REAPER Product Handbook for ERS Altimetry Reprocessed Products](https://earth.esa.int/documents/10174/1511090/Reaper-Product-Handbook-3.1.pdf))


For the following products, the values are provided in the unit of microdegrees and need to be scaled accordingly:

- ATSR
- RA

The coordinates within the ASPS products are given in the unit of millidegrees. 

Furthermore, longitudes need to be converted from the (0-360) range to the (-180 to 180) range for all products.

### Geometry

The ASPS footprint covers one full orbit. The width of the swath is based on the coordinates given by the netCDF variables.

The ATSR AR product contains the pixel coordinates of all pixels along one orbit. The pixel width is 0.5 degrees and there are on average 10 pixels per row. The footprint is calculated by taking the average of the coordinates of every 200 pixels. The width of the swath is [500 km](https://earth.esa.int/web/guest/missions/esa-operational-eo-missions/ers/instruments/atsr). 

For the ATSR NR and TOA products, the width of the swath is based on the coordinates given in the data set records.

For the RA products, the coordinates provided are the orbit coordinates. A continuous polygon having a fictional width of 1 millidegree was chosen to represent the footprint (defined by the offset variable in the OWL):

The number of points per polygon needs to be small enough for the DHuS to be able to handle it. A total number of approximately 400 points was chosen.


