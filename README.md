# Project Description

## Quickstart

### About HELIWARE

Heliware is a Web-GL Powered Geo-Spatial Analytics Platform for developer ,analytics & data Scientist that provides GIS, Web Mapping, and spatial data science tools which help companies to get InSite in just few click using AI, Data Science & Advance Geo-Processing

### Contact

For any query please contact [rajan@heliware.co.in](rajan@heliware.co.in)

### Access Free Api-Key

Get `free` `Api-key` by sign-up on Heliware [Visit Website](https://heliware.co.in/)

## Description About heligeo module

heligeo module provides you high level `Geoprocessing`,`Routing`,`Isochrone` and `Visualization` services.

___
## Routing and Isochrone
* `routes`
* `isochrone`
___
## Geoprocessing
* `polygon_union`
* `polygon_intersection`
* `alias_multistring`
* `point_buffer`
* `line_buffer`
* `point_within_polygon`
* `crop_geometry_data`
* `Polygon_Grid_Creation`
* `Find_Polygon_Center_Point`
___
## Visualization
* `hex_map_from_geojson`
* `hex_map_from_csv`
* `scatter_map_from_geojson`
* `scatter_map_from_csv`
* `line_map_from_geojson`
* `fill_geo_map_from_geojson`
* `density_map_from_geojson`
* `density_map_from_csv`
___
### Requirements
`heligeo-py` is tested over `Python>=3.0`
### Installation

To install from PyPI, simply use pip:  `pip install heligeo`

### How to use
Most of the cases heligeo module accept `Polygon`,`Point`,`Lisestring` data that format must be geojson.

### Usage
#### Basic Example Of Routing Service
By default heligeo support four type of transport mode
* `drive`
* `walk`
* `bike`
* `cycling`

### Output format
Output always `Geojson response`

### Isochrone Service

```

from heligeo import heliRouteService
apikey = ''
longtitude = [88.3639]
latitude = [22.5726]
transport_mode = "drive" 
isochrone_data = heliRouteService.isochrone(apikey,latitude,longtitude,transport_mode)

```

### Routing Service

```
apikey = ''
transport_mode = "drive" 
direction_coordinates = [[88.3639,22.5726],[72.8777,19.0760]] ### user can use multiple points
route_data = heliRouteService.route(apikey,direction_coordinates,transport_mode)

```
### Basic Example Of Geoprocessing Service

* `heliGeoprocessingService.Union()`,`heliGeoprocessingService.Intersection()` function accept multiple polygon data inside a list.
* In this example we shown only 2 polygon data
### Polygon Union Example
```
from heligeo import heliGeoprocessingService
apikey = ''
polygon1 = {"type": "FeatureCollection","features":[{
  "type": "Feature",
  "geometry": {
    "type": "Polygon",
    "coordinates": [[[77.4029103817493, 28.36918941103731, 0.0], [77.40184896262588, 28.3722403721131, 0.0][77.39922678901301, 28.37081966588294, 0.0], [77.40030856003351, 28.36816909494472, 0.0], [74029103817493, 28.36918941103731, 0.0]]]
  }}]}
polygon2 = {"type": "FeatureCollection","features":[{
      "type": "Feature",
      "geometry": {
        "type": "Polygon",
        "coordinates": [[[77.40486731638147, 28.36831967535351, 0.0], [77.40416140548453, 28.37080235923333, 0], [77.40218550684746, 28.    3699755298779, 0.0], [77.40187364471585, 28.36769815943599, 0.0], [740486731638147, 28.36831967535351, 0.0]]]
      }}]}
polygon_list = [polygon1,polygon2]
union_data = heliGeoprocessingService.Union(apikey,polygon_list)


```
![new_img](https://github.com/NandanPattanayak/geopeocessingapi2/blob/main/new.png)
### Polygon Intersection Example

```
from heligeo import heliGeoprocessingService
apikey = ''
polygon1 = {"type": "FeatureCollection","features":[{
  "type": "Feature",
  "geometry": {
    "type": "Polygon",
    "coordinates": [[[77.4029103817493, 28.36918941103731, 0.0], [77.40184896262588, 28.3722403721131, 0.0][77.39922678901301, 28.37081966588294, 0.0], [77.40030856003351, 28.36816909494472, 0.0], [74029103817493, 28.36918941103731, 0.0]]]
  }}]}
polygon2 = {"type": "FeatureCollection","features":[{
      "type": "Feature",
      "geometry": {
        "type": "Polygon",
        "coordinates": [[[77.40486731638147, 28.36831967535351, 0.0], [77.40416140548453, 28.37080235923333, 0], [77.40218550684746, 28.    3699755298779, 0.0], [77.40187364471585, 28.36769815943599, 0.0], [740486731638147, 28.36831967535351, 0.0]]]
      }}]}
polygon_list = [polygon1,polygon2]
intersection_data = heliGeoprocessingService.Intersection(apikey,polygon_list)

```

### PointBuffer Example
* point_list accept multiple points data
```
apikey = ''
point_list = [[88.3639,22.5726]] ### user can user multiple Point inside a list 
area = 100  ### how area user want to conver from this point by default its meter
point_buffer_polygon=heliGeoprocessingService.PointBuffer(apikey,point_list,area)


```

### LineBuffer Example
* linestring_point_list accept multiple linestring.
```
apikey = ''
linestring_point_list = [[[88.3639,22.5726],[88.4143,22.5797]],[[88.2636,22.5958],[88.4789,22.7248]]] ### usecan  user multiple Point inside a list 
area = 100  ### how area user want to conver from this point by default its meter
linestring_buffer_polygon=heliGeoprocessingService.LineBuffer(apikey,linestring_point_list,area)

```
### PointWithinPoly Example
```
apikey = ''
point_geojson_object = {"type":"FeatureCollection","features":[{"type":"Feature","geometry":                {"type":"Point","coordinates":[76.95513342,28.46301607]}}]}
polygon_list = [polygon1,polygon2]
point_inside_poly = heliGeoprocessingService.PointWithinPoly(apikey,point_geojson_object,polygon_list)


```

### AliasLinestring Example
```
apikey = ''
linestring_geojson_object = {"type": "FeatureCollection","features":[{"type": "Feature","geometry{"type":"LineString",
    "coordinates": [
      [88.3639,22.5726],[88.4143,22.5797]
    ]}}]}
gap = 100 #gap between multiple linestring(meter)
quantity = 100 ## how many line string u need 
alias_linestring_data = heliGeoprocessingService.AliasLinestring(apikey,linestring_geojson_object,gap,quantity)

```
### CropGeometryData
* `CropGeo` fuction accept a `Polygon GeoJson` data and `crop` other geometry data based on the `Polygon Size`.
* `CropGeo` accept `bb={}` contain `Polygon Geojson` data in which size u want to crop other geometry and `gd={[]}` contain all the getometry data which u want to `crop` `gd` `list` contain `Polygon`,`Linestring` and `point` data. Data must be `GeoJson format`.
* `CropGeo` supported only `Polygon`,`Linestring` and `point` data in `Geojson` format

```
apikey = ''
bb = {"type":"FeatureCollection","features":[{"type":"Feature","geometry":{"type":"Polygon","coordinates":[[[76.76781345955712,30.524042786522788],[76.76658493660516,30.521411933136562],[76.76638374787312,30.520437335225605],[76.76812128413364,30.519991051100444],[76.76935817172217,30.5235212331106],[76.76781345955712,30.524042786522788]]]},"properties":{"PERIMETER":"1.166km","ENCLOSED_AREA":"0.0727sqkm"}}]}

gd = [{"type":"FeatureCollection","features":[{"type":"Feature","geometry":{"type":"LineString","coordinates":[[76.76605941690902,30.521077391710715],[76.76854013805993,30.52031431912859],[76.76854013805993,30.52031431912859]]},"properties":{"LENGTH":"252.68m","BEARING":"1093333.9"}},{"type":"Feature","geometry":{"type":"LineString","coordinates":[[76.76629027392768,30.521865657532633],[76.76849050129871,30.521044858531493],[76.768764809871,30.520962819202154],[76.768764809871,30.520962819202154]]},"properties":{"LENGTH":"257.8m","BEARING":"112514.9"}},{"type":"Feature","geometry":{"type":"LineString","coordinates":[[76.76897591153649,30.52205540468611],[76.76691180534269,30.522839498623096],[76.76691197785424,30.522849031168167]]},"properties":{"LENGTH":"217.4m","BEARING":"2935656.9"}},{"type":"Feature","geometry":{"type":"LineString","coordinates":[[76.76727709618594,30.523549659635112],[76.76936689485044,30.52278710560935],[76.76936689485044,30.52278710560935]]},"properties":{"LENGTH":"217.66m","BEARING":"1125115.1"}}]}]

crop_data = heliGeoprocessingService.CropGeo(apikey,bb,gd)

```

### Polygon Grid Creation Example
* `PolyGrid` function accept `three` parameter `apikey`, `polygon_geo_json_data` and  `grid-size`.
* Based on the grid size `PolyGrid` function break down the `parent poly` into `small grids`.
* `PolyGrid` accept only `polygon` geojson data.

```
apikey = ''

polygon_geo_json_data = {"type":"FeatureCollection","features":[{"type":"Feature","properties":{},"geometry":{"type":"Polygon","coordinates":[[[76.9720448,28.4914468],[76.9734664,28.490094],[76.9745038,28.4891069],[76.9777595,28.4865896],[76.9832406,28.4847617],[76.9877826,28.4817885],[76.9994099,28.4931639],[76.9958932,28.49571],[76.9958867,28.4995722],[76.993081,28.5026631],[76.9897562,28.5047863],[76.9854207,28.5071706],[76.979788,28.501845],[76.9762078,28.4984432],[76.9720448,28.4914468]]]}}]}

gridsize = 3 # in meter user change value as per user choice
poly_grid_data = heliGeoprocessingService.PolyGrid(apikey,polygon_geo_json_data,gridsize)
```
### Find Polygon Center Point Example
* `PolyCenter` accept `two` `parameter` `apikey` and `list_of_polygon_data=[polygeojson1,polygeojson1...n]`.

* `PolyCenter` function accept only `multiple polygon data` in `geojson` format.

* `list_of_polygon_data` its a list of multiple polygon data that must be geojson format
```
apikey = ''

list_of_polygon_data = [{"type":"FeatureCollection","features":[{"type":"Feature","properties":{},"geometry":{"type":"Polygon","coordinates":[[[76.9720448,28.4914468],[76.9734664,28.490094],[76.9745038,28.4891069],[76.9777595,28.4865896],[76.9832406,28.4847617],[76.9877826,28.4817885],[76.9994099,28.4931639],[76.9958932,28.49571],[76.9958867,28.4995722],[76.993081,28.5026631],[76.9897562,28.5047863],[76.9854207,28.5071706],[76.979788,28.501845],[76.9762078,28.4984432],[76.9720448,28.4914468]]]}}]},{"type":"FeatureCollection","features":[{"type":"Feature","properties":{},"geometry":{"type":"Polygon","coordinates":[[[76.9720448,28.4914468],[76.9734664,28.490094],[76.9745038,28.4891069],[76.9777595,28.4865896],[76.9832406,28.4847617],[76.9877826,28.4817885],[76.9994099,28.4931639],[76.9958932,28.49571],[76.9958867,28.4995722],[76.993081,28.5026631],[76.9897562,28.5047863],[76.9854207,28.5071706],[76.979788,28.501845],[76.9762078,28.4984432],[76.9720448,28.4914468]]]}}]},{"type":"FeatureCollection","features":[{"type":"Feature","properties":{},"geometry":{"type":"Polygon","coordinates":[[[76.9720448,28.4914468],[76.9734664,28.490094],[76.9745038,28.4891069],[76.9777595,28.4865896],[76.9832406,28.4847617],[76.9877826,28.4817885],[76.9994099,28.4931639],[76.9958932,28.49571],[76.9958867,28.4995722],[76.993081,28.5026631],[76.9897562,28.5047863],[76.9854207,28.5071706],[76.979788,28.501845],[76.9762078,28.4984432],[76.9720448,28.4914468]]]}}]}]

poly_center_point = heliGeoprocessingService.PolyCenter(apikey,list_of_polygon_data)

```

## Basic Example Of Visualization Service


### Hexagon Map
* User Can Select Different type of `BaseMap` Like `basic`, `streets`,`outdoors`, `light`, `dark`, `satellite`, or `satellite-streets`
* User can Create `hex_map` from `.geojon` and `.csv` file
* File Must be contain `geometry` data
* `hex_map_from_geojson` funtion accepty `.geojson` file with other parameter and `hex_map_from_csv` accept `.csv` file with other parameter.
* `hex_map_from_geojson` accept `apikey`,`file_path`,`hover_properties`,`basemap_style`,`hexagon_quantity`,`zoom_level`
* `hex_map_from_csv` accept `apikey`,`file_path`,`column name from csv file that contain latitude value`,`column name from csv file that contain longtitude value`,`hover_properties`,`basemap_style`,`hexagon_quantity`,`zoom_level`
* As of Now `heligeo` module able to visualize only `one propertie ` with their corrosponding `Lat`,`Long` value
* `Base_map=''`
* Use `res.show()` to visualize the data into web. 
* for `hex_map_from_geojson` user dont need to pass this two parameter  `column name that contain latitude value`,`column name that contain longtitude value` we create these two value as our own.
#### Example 
```
from heligeo import heliVisualizationService
apikey=''
file_path = '' 
latitude_value_col_name = ''
longtitude_value_col_name = ''
hover_properties = ''
base_map = ''
hexagan_quantity = 20  
zoom_level = 16
h = heliVisualizationService.hex_map_from_csv(apikey,file_path,latitude_value_col_name,longtitude_value_col_name,hover_properties,base_map,hexagan_quantity,zoom_level)
h.show()

h = heliVisualizationService.hex_map_from_geojson(apikey,file_path,hover_properties,base_map,hexagan_quantity,zoom_level)
h.show()

```


### Scatter Map
* User Can Select Different type of `BaseMap` Like `basic`, `streets`, `outdoors`, `light`, `dark`, `satellite`, or `satellite-streets`
* User can Create `scatter_map` from `.geojson` and `.csv` file
* File Must be contain `geometry` data
* `scatter_map_from_geojson` funtion accept `.geojson` file with other parameter and `scatter_map_from_csv` accept `.csv` file with other parameter.
* `scatter_map_from_geojson` accept `apikey`,`file_path`,`hover_properties`,`basemap_style`,`zoom_level`
* `scatter_map_from_csv` accept `apikey`,`file_path`,`column name from csv file that contain latitude value`,`column name from csv file that contain longtitude value`,`hover_properties`,`basemap_style`,`zoom_level`
* As of Now `heligeo` `Visualization` module able to visualize only `one propertie ` with their corrosponding `Lat`,`Long` value

* Use `res.show()` to visualize the data into web. 
* for `scatter_map_from_geojson` user dont need to pass this two parameter  `column name that contain latitude value`,`column name that contain longtitude value` we create these two value as our own.

#### Example 
```
from heligeo import heliVisualizationService
apikey=''
file_path = '' 
latitude_value_col_name = ''
longtitude_value_col_name = ''
hover_properties = ''
base_map = ''  
zoom_level = 16
h = heliVisualizationService.scatter_map_from_csv(apikey,file_path,latitude_value_col_name,longtitude_value_col_name,hover_properties,base_map,zoom_level)
h.show()

h = heliVisualizationService.scatter_map_from_geojson(apikey,file_path,hover_properties,base_map,zoom_level)
h.show()


```





### Density Map
* User Can Select Different type of `BaseMap` Like `basic`, `streets`, `outdoors`, `light`, `dark`, `satellite`, or `satellite-streets`
* User can Create `density_map` from `.geojson` and `.csv` file
* File Must be contain `geometry` data
* `density_map_from_geojson` funtion accept `.geojson` file with other parameter and `density_map_from_csv` accept `.csv` file with other parameter.
* `density_map_from_geojson` accept `apikey`,`file_path`,`hover_properties`,`basemap_style`,`zoom_level`
* density_map_from_csv` accept `apikey`,`file_path`,`column name from csv file that contain latitude value`,`column name from csv file that contain longtitude value`,`hover_properties`,`basemap_style`,`zoom_level`
* As of Now `heligeo` `Visualization` module able to visualize only `one propertie ` with their corrosponding `Lat`,`Long` value

* Use `res.show()` to visualize the data into web. 
* for `density_map_from_geojson` user dont need to pass this two parameter  `column name that contain latitude value`,`column name that contain longtitude value` we create these two value as our own.

#### Example 
```
from heligeo import heliVisualizationService
apikey=''
file_path = '' 
latitude_value_col_name = ''
longtitude_value_col_name = ''
hover_properties = ''
base_map = ''  
zoom_level = 16
h = heliVisualizationService.density_map_from_csv(apikey,file_path,latitude_value_col_name,longtitude_value_col_name,hover_properties,base_map,zoom_level)
h.show()

h = heliVisualizationService.density_map_from_geojson(apikey,file_path,hover_properties,base_map,zoom_level)
h.show()

```


### Line Map
* User Can Select Different type of `BaseMap` Like `basic`, `streets`, `outdoors`, `light`, `dark`, `satellite`, or `satellite-streets`
* User can Create `line_map` from `.geojson`.
* `line_map_from_geojson` funtion accept `.geojson` file with other parameter.
* `density_map_from_geojson` accept `apikey`,`file_path`,`hover_properties`,`basemap_style`,`zoom_level`
* As of Now `heligeo` `Visualization` module able to visualize only `one propertie ` with their corrosponding `Lat`,`Long` value
* Use `res.show()` to visualize the data into web. 

#### Example 
```
from heligeo import heliVisualizationService
apikey=''
file_path = '' 
hover_properties = ''
base_map = ''  
zoom_level = 15
h = heliVisualizationService.line_map_from_geojson(apikey,file_path,hover_properties,base_map,zoom_level)
h.show()

```

### Fill Geometry With Color
* User Can Select Different type of `BaseMap` Like `open-street-map`, `carto-positron`, `carto-darkmatter`, `stamen-terrain`, `stamen-toner` or `stamen-watercolor`
* User can fill a `Geometry` with different color and `Visualize` on map.
* `fill_geo_map_from_geojson` funtion accept `.geojson` file with other parameter.
* `fill_geo_map_from_geojson` accept `apikey`,`file_path`,`color`,`basemap_style`,`zoom_level`
* As of Now `heligeo` `Visualization` module able to visualize only `one propertie ` with their corrosponding `Lat`,`Long` value
* Use `res.show()` to visualize the data into web. 

#### Example 
```
from heligeo import heliVisualizationService
apikey=''
file_path = '' 
color = ''
base_map = ''  
zoom_level = 15
h = heliVisualizationService.fill_geo_map_from_geojson(apikey,file_path,color,base_map,zoom_level)
h.show()

```



## License
???? 2021 HELIWARE

This repository is licensed under the MIT license. See LICENSE for details.