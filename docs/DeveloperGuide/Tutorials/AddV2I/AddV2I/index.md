# Add V2I

## 1. Add V2I prefab

![add prefab](add_prefab.gif)

## 2. Select EGO transform
   
![select ego transform 1](select_ego_transform_1.png)
![select ego transform 2](select_ego_transform_2.gif)
![select ego transform 3](select_ego_transform_3.png)

## 3. Configure

Name                            | Type      | Description
------------------------------- | --------- | -----------
Output Hz                       | int       | Topic publication frequency
Ego Vehicle Transform           | transform | Ego Vehicle object transform 
Ego Distance To Traffic Signals | double    | Maximum distance between Traffic Light and Ego
Traffic Signal ID               | enum      | Possibility to select if as `traffic_signal_id` field in msg is `Relation ID` or `Way ID`
Traffic Signals Topic           | string    | Topic name

!!! note 
    V2I feature can be used as Traffic Light ground truth information, and for that usage `Way ID` is supposed to be selected.