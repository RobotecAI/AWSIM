To add `RandomTraffic` to the `Environment`, it is necessary to load elements from the *lanelet2*.
As a result of loading, `TrafficLanes` and `StopLines` will be added to the scene. Details of these components can be found [here](../../../../UserGuide/ProjectGuide/Components/RandomTrafficSimulator/).

!!!warning
    Before following this tutorial make sure you have added an [Environment Script](../../AddANewEnvironment/AddAEnvironment/#add-an-environment-script) and set a proper `MGRS` offset position. This position is used when loading elements from the *lanelet2*!

1. Click on the `AWSIM` button in the top menu of the Unity editor and navigate to `AWSIM -> Random Traffic -> Load Lanelet`

    ![load lanelet gif](load_lanelet.gif)

2. In the window that pops-up select your osm file, change some Waypoint Settings to suit your needs and click `Load`

    ![load lanelet gif](load_lanelet2.gif)

    Waypoint Settings explanation:

    - Resolution: resolution of resampling. Lower values provide better accuracy at the cost of processing time
    - Min Delta Length: minimum length(m) between adjacent points
    - Min Delta Angle: minimum angle(deg) between adjacent edges. Lowering this value produces a smoother curve

3. Traffic Lanes and Stop Lanes should occur in the Hierarchy view.
If they appear somewhere else in your Hierarchy tree, then move them into the `Environment` object

## Complete loaded TrafficLanes
The Traffic Lanes that were loaded should be configures accordingly to the road situation.

## How to test
<!-- TODO -->

## Add a StopLine manually
When something goes wrong when loading data from *lanelet2* or you just want to add another StopLine manually please do the following

1. Add a new GameObject *StopLine* in the *StopLines* parent object.

    ![add stop line object](add_stop_line.gif)

1. Add a StopLine Script by clicking 'Add Component' and searching for `Stop Line`.

    ![add component](add_stop_line_add_script.gif)

    ![search stop line](stop_line_search.png)

    So far your Stop Line should look like the following

    ![stop line inspector view](stop_line_inspector.png)

1. Set the position of points `Element 0` and `Element 1`

    These Elements are the two end points of a Stop Line.
    The Stop Line will span between these points.

    You don't need to set any data in the 'Transform' section as it is not used anyway.

    !!! warning "StopLine coordinate system"
        Please note that the Stop Line Script operates in the global coordinate system.
        The transformations of StopLine *Object* and its parent *Objects* won't affect the Stop Line.

        ??? example
            In this example you can see that the Position of the *Game Object* does not affect the position and orientation of the Stop Line.

            For a Game Object in the center of the coordinate system.

            ![stop line in default position](stop_line_position11.png)

            The stop Line is in the specified position.

            ![stop line in default position](stop_line_position12.png)

            However with the *Game Object* shifted in X axis.

            ![stop line in new position](stop_line_position21.png)

            The Stop Line stays in the same position as before, not affected by any transformations happening to the *Game Object*.

            ![stop line in new position](stop_line_position22.png)

1. Select whether there is a Stop Sign.

    Select the `Has Stop Sign` tick-box confirming that this Stop Line has a Stop Sign.
    The Stop Sign can be either vertical or horizontal.

1. Configure is selection of a Traffic Light.

    The last thing to configure is a Traffic Light.
    You need to select one only when the Stop Line is right in front of a [Traffic Intersection](../../../../UserGuide/ProjectGuide/Components/RandomTrafficSimulator/) that has a Traffic Lights.

    Select from the drop-down menu the Traffic Light that is on the Traffic Intersection and is facing the vehicle that would be driving on the Traffic Lane connected with the Stop Line you are configuring.

    In other words select the right Traffic Light for the Lane on which your Stop Line is placed.

    !!! tip "Select Traffic Lights visually"
        If you have a lot of Traffic Lights it can be challenging to add them from the list.
        You can select them visually from the Scene the same as you had selected Traffic Lanes in the [Random Traffic Simulator](../AddARandomTrafficSimulatorScript/#add-spawnable-lanes).

1. Configure the Traffic Lane,

    Every Stop Line has to be connected to a Traffic Lane.
    This is done in the Traffic Lane configuration.
    For this reason please check the [Traffic Lane section](#add-a-trafficlane-manually) for more details.

## Add a TrafficLane manually
It is possible that something may go wring when reading a *lanelet2* and you need to add an additional Traffic Lane or you just want to add it.
To add a Traffic Lane manually please follow the steps below.

1. Add a new *Game Object* called `TrafficLane` into the `TrafficLanes` parent *Object*.

    ![traffic lane add object](traffic_lane_add_object.gif)

2. Click the 'Add Component' button and search for the `Traffic lane` script and select it.

    ![traffic lane add component](traffic_lane_add_component.gif)

    ![traffic lane search](traffic_lane_search.png)

    So far your traffic lane should look like the following.

    ![traffic lane configuration](traffic_lane_configuration.png)

3. Configure the 'Waypoints' list.

    This list is an ordered list of nest points defining the Traffic Lane.
    When you want to add a waypoint to a Traffic Lane just click on the `+` button or specify the number of waypoints on the list in the field with number to the right from 'Waypoints' identifier.

    The order of elements on this list determines how waypoints are connected.

    !!! warning "Traffic Lane coordinate system"
        Please note that the Traffic Lane waypoints are located in the global coordinate system, any transformations set to a *Game Object* or paren *Objects* will be ignored.

        This behavior is the same as with the Stop Line.
        You can see the example provided in the [Stop Line tutorial](#add-a-stopline-manually).

    !!! info "General advice"
        - Two waypoints should not be too far away from each other.
        - When creating a turn that is a curvature please keep in mind the angle that is created between two next waypoints connected.
            The angles should be fairly small - this will translate to a smooth motion of vehicles.

4. Select The Turn Direction.

    This field describes what are the vehicles traveling on ths Traffic Lane doing in reference to other Traffic Lanes.
    You need to select whether the vehicles are
    
    - Driving straight (`STRAIGHT`)
    - Turning right (`RIGHT`)
    - Turning left (`LEFT`)

5. Configure Next Lanes.

    Into the Next Lanes list you need to add all Traffic Lanes that have their beginning in the end of this Traffic Lane.
    In other words if the vehicle can choose where he wants to drive (e.g. drive straight or drive left with choice of two different Traffic Lines)

    ??? example
        Lets consider the following Traffic Intersection.

        ![traffic lane situation](traffic_lane_situation.png)

        In this example we will consider the Traffic Lane driving from the bottom of the screen and turning right.
        After finishing driving in this Traffic Lane the vehicle has a choice of 4 different Traffic Lanes each turning into different lane on the parallel road.

        All 4 Traffic Lanes are connected to the considered Traffic Lane.
        This situation is reflected in the Traffic Lane configuration shown below.

        ![traffic lane description](traffic_lane_description.png)

    !!! tip "Select Traffic Lanes visually"
        If you have a lot of Traffic Lanes it can be challenging to add them from the list.
        You can select them visually from the Scene the same as you had selected Traffic Lanes in the [Random Traffic Simulator](../AddARandomTrafficSimulatorScript/#add-spawnable-lanes).

6. Configure Previous Lanes.

    Traffic Lane has to have previous Traffic Lanes configured.
    This is done in the exact same way as configuring next lanes which was shown in the previous step.
    Please do the same but add Traffic Lanes that are before the configured one instead of the ones after.

7. Configure Right Of Way Lanes.

    The Right Of Way Lanes is a list of Traffic Lanes that have a priority over the configured one.
    The process of adding the Right of way lanes is the same as with adding Nest Lanes.
    For this reason we ask you to see that step for detailed description on how to do this.

    ??? example
        In this example lets consider the Traffic Lane highlighted in blue from the Traffic Intersection below.

        ![right of way situation](traffic_lane_right_of_way_situation.png)

        This Traffic Lane has to give way to all Traffic Lanes highlighted on yellow.
        This means all of the yellow Traffic Lanes have to be added to the 'Right Of Way Lanes' list which is reflected on the configuration shown below.

        ![right of way configuration](traffic_lane_right_of_way_configuration.png)

8. Add Stop Line.

    This step is necessary only when at the end of the configured Traffic Lane the Stop Line is present.
    If so please select the correct Stop Line from the drop-down list.

    !!! tip "Select Stop Line visually"
        If you have a lot of Stop Lines it can be challenging to add them from the list.
        You can select them visually from the Scene the same as you had selected Traffic Lanes in the [Random Traffic Simulator](../AddARandomTrafficSimulatorScript/#add-spawnable-lanes).

9. Add Speed Limit.

    In the field called `Speed limit` simply write the speed limit that is in effect on the configured Traffic Lane.

10. Set the Right of Ways

    To make the Right Of Ways list you configured earlier take effect simply click the 'Set RightOfWays' button.