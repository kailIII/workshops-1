Advanced GeoServer workshop
===========================

The following instructions will show how to prepare a fresh OpenGeo Suite installation for the Advanced GeoServer workshop.


1. Install the OpenGeo Suite. The software is not included in this bundle.

2. Create a PostGIS database called earth:
   createdb earth
   Turn on the PostGIS extension with SQL: 
   create extension postgis

3. Load all shapefiles in the data/earth/ directory into PostGIS using pgShapeLoader or psql:
   for f in *shp; do shp2pgsql -g geom -s 4326 $f ${f/.shp/} | psql earth

4. Create a workspace in GeoServer called "earth". For the URI, you must use http://earth.opengeo.org.

5. Create a PostGIS store in GeoServer in the earth workspace called "earth" . Point it at the PostGIS database of the same same.

6. Load each table from the PostGIS store into GeoServer as a layer using the same names as the tables.

7. Upload each SLD file in the styles/earth/ directory as a new style in GeoServer and associate each with its namesake layer. The first letter of the style names should be capitalised.

8. Load shadedrelief.tif as a GeoTIFF datastore and layer (again in the earth workspace).

9. Create a layer group called "earth" that contains each of the layers loaded. Suggested order: shadedrelief, ocean, cities, coastline, countries, rivers. This should NOT be in workspace "earth".

10. Create a PostGIS database called advanced
    createdb advanced
    Turn on the PostGIS extension with SQL: 
    create extension postgis

11. Load all shapefiles in the data/advanced/ directory into PostGIS using pgShapeLoader or psql:
    for f in *shp; do shp2pgsql -g geom -s 4326 $f ${f/.shp/} | psql advanced


All other loading and configuring will be done as part of the workshop.

For more information, please contact us at http://opengeo.org/about/contact/ .


----

Note: The spatial data files contained in this package are taken from http://naturalearthdata.com/. 
