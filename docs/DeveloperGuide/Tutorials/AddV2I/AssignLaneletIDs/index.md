# Assign Lanelet2 WayID and RelationID to TrafficLight object

1. Load items from lanelet2 following [the instruction](../../../../DeveloperGuide/Tutorials/AddARandomTraffic/LoadItemsFromLanelet/index.md)

2. Verify if `Traffic Light Lanelet ID` component has been added to `Traffic Light` game objects.
![verify traffic light lanelet id](verify_traffic_light_lanelet_id.png)

3. Verify if `WayID` and `RelationID` has been correctly assigned. You can use [Vector Map Builder](https://tools.tier4.jp/vector_map_builder_ll2/) as presented below
![verify lanelet ids](verify_lanelet_ids.png)

## Add manually `Traffic Light Lanelet ID` component

If for some reason, `Traffic Light Lanelet ID` component is not added to `Traffic Light` object.

### 1. Add component manually
![add component 1](add_component_1.gif)

### 2. Fill Way ID
![add component 2](add_component_2.gif)

### 3. Fill Relation ID
![add component 3](add_component_3.gif)

