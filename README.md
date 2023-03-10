# Google Earth Engine raster to BigQuery CSV convertion project

Free data catalog and cloud processing system Google Earth Engine (GEE) provides a lot of of geospatial datasets. This project uses a chunked downloading to extract big rasters, even dozens of gigabyte each from Google Earth Engine. For an example, that is possible to download 500 GB raster in 12-24 hours.

For Google Earth Engine (GEE) access the service account key required (it's named /root/gee-export.json in the scripts), to create your own one
follow the link [Create and register a service account to use Earth Engine](https://developers.google.com/earth-engine/guides/service_account)

## GeoTIFF to BigQuery CSV convertion tool

Use provided script [geotif-to-bqcsv.py](scripts/geotif-to-bqcsv.py) to convert WGS 84 GeoTIFF files to BigQuery CSV data and table schema:
```
./geotif-to-bqcsv.py GeoTIFF_file [CSV_file]
```
or for batch conversion:
```
find . -name '*.tif' -print0 | parallel -0 geotif-to-bqcsv.py '{}' '{}'.csv
```

With just mandatory first argument the script returns corresponding BigQuery table schema only. With the optional second argument this script
converts the entire GeoTIFF file to CSV output into the specified file and also prints the schema too.

## [WorldPop Global Project Population Data: Estimated Residential Population per 100x100m Grid Square](https://developers.google.com/earth-engine/datasets/catalog/WorldPop_GP_100m_pop)

See [WorldPop.sh](scripts/WorldPop.sh) to extract data for 2020 year in WGS84 coordinates.

![](https://mw1.google.com/ges/dd/images/WorldPop_GP_100m_pop_sample.png)

## [MOD17A3HGF.006: Terra Net Primary Production Gap-Filled Yearly Global 500m](https://developers.google.com/earth-engine/datasets/catalog/MODIS_006_MOD17A3HGF)

See [AnnualNPP.sh](scripts/AnnualNPP.sh) to extract the entire dataset and convert it into WGS84 coordinates.

![](https://mw1.google.com/ges/dd/images/MODIS_006_MOD17A3HGF_sample.png)

## [GFS: Global Forecast System 384-Hour Predicted Atmosphere Data](https://developers.google.com/earth-engine/datasets/catalog/NOAA_GFS0P25)

See [GFS.sh](scripts/GFS.sh) to extract data for date "2021/04/13" and forecasting interval 384 hours in WGS84 coordinates.

![](https://mw1.google.com/ges/dd/images/NOAA_GFS0P25_sample.png)
