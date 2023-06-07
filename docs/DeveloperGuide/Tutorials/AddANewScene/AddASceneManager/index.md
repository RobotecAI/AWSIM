`SceneManager` is available as a prefab in the *AWSIM* project.
The prefab is located in the directory `Assets/AWSIM/Prefabs` in the *Project* tree.

`SceneManager` (`RGLSceneManager`) is used for synchronizing model data between *Unity* and [RobotecGPULidar](https://github.com/RobotecAI/RobotecGPULidar). You can read more about this in this [section](../../../../UserGuide/ProjectGuide/ExternalLibraries/RGLUnityPlugin/). 

!!! warning "Usage requirements"
    Before adding `SceneManager`, check that all objects in the scene meet the requirements for use - it is described [here](../../../../UserGuide/ProjectGuide/ExternalLibraries/RGLUnityPlugin/).

## Add a prefab to scene
You can add `SceneManager` as a prefab, or if you prefer, you can add is [as a component](#add-a-component).

To add a `SceneManager` prefab to a scene you need to

1. Open the scene

    ![open_scene](open_scene.png)

1. Find the prefab in the project (`Assets/AWSIM/Prefabs` directory)

    ![scene_manager_prefab_location](scene_manager_prefab_location.png)

1. Drag the prefab into a Hierarchy view

    ![add_prefab_to_scene](add_scene_manager.gif)

1. Rename this prefab to something like `AutowareSimulation` or just `Simulation` with preferred prefix or suffix and place all your simulation *GameObjects* as children (if you don't have any yet, this is where you will be placing them).

    ![Add scene manager to scene gif](add_scene_manager2.gif)

    ![Add scene manager to scene gif](add_scene_manager3.gif)

## Add a component 
When you already have a parent `Simulation` object it is possible to add a `SceneManager` as a component which will be described in this section.

1. Click on the `Simulation` *Object*

1. Click 'Add Component', search for `Scene Manager` and select it.

    ![scene manager add](scene_manager_add_component.gif)

    ![scene manager search](scene_manager_search.png)
    

## Selection of interaction strategies (Mesh Source)
There are three possible interaction strategies for obtaining *3D* models from *GameObjects*. Details about each source are described [here](../../../../UserGuide/ProjectGuide/ExternalLibraries/RGLUnityPlugin/).

Please see the following on how to select the preferred strategy.

![scene_manager_only_colliders](scene_manager_only_colliders.gif)