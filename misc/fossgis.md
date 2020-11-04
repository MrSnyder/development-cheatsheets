# FOSSGIS

## Imposm Cheatsheet

* Imports OpenStreetMap data into PostgreSQL/PostGIS databases.
* [https://imposm.org/](https://imposm.org/) 

  ```bash
  imposm  import -config imposm_config/config.json -read imposm_data/detmold-regbez-latest.osm.pbf -write -overwritecache -deployproduction
  ```

## GeoServer

### Behind reverse proxy

* [User Proxy Headers for URL](https://docs.geoserver.org/stable/en/user/configuration/globalsettings.html#use-headers-for-proxy-url)
* Apache: `RequestHeader set "Forwarded" "host=hostname;proto=https"`

## ETF

```bash
unzip functx-1.0.xar -d etf/ds/db/repo/BaseXRepo
```

* [Starting a Test Run with the API](http://docs.etf-validator.net/v2.0/Developer_manuals/WEB-API.html#_starting_a_test_run_with_the_api)

