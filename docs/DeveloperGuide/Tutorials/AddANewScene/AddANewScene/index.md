!!! Draft-note
    - Add a ClockPublisher (ros2 topic, qos)
    - Add MainCamera
        - Camera component (**screen**, hyperlinks, configure fov)
        - Follow Camera Script (target, parameters, example - **screen**)
    - Add a Vehicle (exists prefabs, positioning on the scene, **gifs**)
    - Add a Scene Manager Script (hyperlink)
    - Add a Environment prefab (hyperlink)

## Add a ClockPublisher
1. Add a child *Object* to a *Simulation*.

    <!-- ![clock publisher object](clock_publisher_add_object.gif) -->
    <img src=clock_publisher_add_object.gif width=600px>

1. Click 'Add Component' button, search for `Clock Publisher` Script and select it.

    ![clock publisher add script](clock_publisher_add_component.gif)

    ![clock publisher search](clock_publisher_search.png)

1. Finally you can configure your Clock Publisher by changing the topic or Quality of Service (qos) settings.

    !!!danger
        Change these settings only when you know what you are doing, otherwise you can break the communication between the simulation and autonomous driving software.

## Add MainCamera
To add a Main Camera please do the following

1. Add a child *Object* to a *Simulation* called 'Main Camera'

    <!-- ![main camera add component](main_camera_add_component.gif) -->
    <img src=main_camera_add_component.gif width=600px>

1. Click 'Add Component' button, search for `Camera` and select it.

    ![main camera add component](main_camera_add_component2.gif)
    <!-- <img src=main_camera_add_component2.gif width=600px> -->

    ![camera search](camera_search.png)

    !!! note
        With the `Camera` component there should automatically be added a `HD Additional Camera Data` Script as seen below.

        ![additional camera data](hd_additional_camera_data.png)

    In this step you can adjust some of the camera setting if you wish.
    For more information please visit the [official Unity documentation](https://docs.unity3d.com/Manual/class-Camera.html).

1. Click 'Add Component' button, search for `Audio Listener` and select it.

    This step is identical as the step before, just search for a different component as seen below.

    ![audio listener search](audio_listener_search.png)

1. Click 'Add Component' button, search for `Follow Camera` Script and select it.

    This step is identical as the step before, just search for a different component as seen below.

    ![follow camera search](follow_camera_search.png)

    Now you will need to configure the `Follow Camera` Script

    - From the `Target` drop-down menu select the transformation of the vehicle you want the camera to follow.
    - Configure the distance of the camera relative to the vehicle.
        The final configuration should look similar to the example below.

        ![follow camera configuration](follow_camera_configuration.png)

??? example "Example configuration"
    After following all the steps above your Main Camera should look similar to the one below.

    ![main camera example configuration](main_camera_example_configuration.png)

## Add a Vehicle
<!-- TODO -->

## Add a Scene Manager Script
Tutorial on how to add a `SceneManager` Script can be found [here](../AddASceneManager/).

## Add an Environment prefab
<!-- TODO -->