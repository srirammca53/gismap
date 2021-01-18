# README

gismap
Created an application with Postgresql database # completed

Ruby 2.3.1 and rails 4.1 version # completed

Installed postgis for handling the GIS data # completed

Configuring the database yml and created database gismap _development # completed

Setup of GIS data is completed by running gis:setup command # completed

Gems used : gem 'activerecord-postgis-adapter' # completed

Creating table with below # pending create_table :my_spatial_table do |t| t.column :shape1, :geometry t.geometry :shape2 t.line_string :path, srid: 3785 t.st_point :lonlat, geographic: true t.st_point :lonlatheight, geographic: true, has_z: true end

and data types understood by PostGIS and exposed by activerecord-postgis-adapter: # pending • :geometry -- Any geometric type • :st_point -- Point data • :line_string -- LineString data • :st_polygon -- Polygon data • :geometry_collection -- Any collection type • :multi_point -- A collection of Points • :multi_line_string -- A collection of LineStrings • :multi_polygon -- A collection of Polygons

Configurations as below : # pending

RGeo::ActiveRecord::SpatialFactoryStore.instance.tap do |config|

By default, use the GEOS implementation for spatial columns.
config.default = RGeo::Geos.factory_generator

But use a geographic implementation for point columns.
config.register(RGeo::Geographic.spherical_factory(srid: 4326), geo_type: "point") end

add_index :my_table, :lonlat, using: :gist
or
change_table :my_table do |t| t.index :lonlat, using: :gist end

Running the application and deploy to Heroku. #pending
