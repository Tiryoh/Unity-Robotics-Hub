# Visualizing Custom Messages

## Introduction

The Default Visualization Suite provided in the Message Visualizations package contains visualizers for many common message types, but many projects use custom messages to package multiple connected ROS messages under a single topic. Visualizing incoming and outgoing message information can be useful in understanding sensor readings and control signals, or it can help with debugging coordinate transformations or offset values.

The [Pick-and-Place](../pick_and_place/README.md) tutorial utilizes a custom message type, NiryoMoveitJoints, to describe the joint positions as well as the target object and goal poses. This tutorial will step through how to write a visualizer for this custom message type in order to visually inspect the values being published.

**Table of Contents**
- [Visualizing Custom Messages](#visualizing-custom-messages)
  - [Introduction](#introduction)
  - [Prerequisites](#prerequisites)
  - [Creating a New Visualizer](#creating-a-new-visualizer)
    - [Drawing the UI Window](#drawing-the-ui-window)
    - [Adding Customization Parameters](#adding-customization-parameters)
    - [Drawing a Pose](#drawing-a-pose)
    - [Drawing a Robot](#drawing-a-robot)
  - [More with Message Visualizations](#more-with-message-visualizations)

---

## Prerequisites

- This tutorials assumes you have completed at least Parts [1](../pick_and_place/1_urdf.md) and [2](../pick_and_place/2_ros_tcp.md) of the [Pick-and-Place](../pick_and_place/README.md) tutorial, such that you have completed ROS–Unity integration and can successfully publish a message from Unity to ROS. The following steps will be using this Unity project.

## Creating a New Visualizer

1. From the Unity Hub, open the `PickAndPlaceProject`.

2. If you have not already added the Message Visualizations package in your Unity project, follow the [Installation Steps](../quick_setup.md).

3. To start writing a custom visualizer, start by making a new script named `NiryoMoveitJointsVisualizer`.

    > To create a new script, right click in the Project window, and select `Create > C# Script`.

    > TODO: For the completed script, see...

    Creating a new script will create a template that automatically inherits from [MonoBehaviour](https://docs.unity3d.com/Manual/class-MonoBehaviour.html) with the basic using directives. To turn this script into a visualizer, we'll need to reference the additional required packages. This includes the generated messages, ROS Geometry for coordinate conversions, URDF importer for robot drawings, and, of course, message visualizations.

    At the top of the script, import these namespaces:

    ```csharp
    using RosMessageTypes.NiryoMoveit;                  // Generated messages
    using Unity.Robotics.MessageVisualizers;            // Message visualizations
    using Unity.Robotics.ROSTCPConnector.ROSGeometry;   // Coordinate space conversions
    using Unity.Robotics.UrdfImporter;                  // URDF classes
    ```

    You now have access to the necessary classes and functions for this visualization. A visualizer that has both a GUI window and a 3D drawing for a specific message type should inherit from the `DrawingVisualizer<T>` class--do this now by replacing the `MonoBehaviour` class to `DrawingVisualizer<NiryoMoveitJointsMsg>`.

    > TODO: For more information about the Visualizer classes, learn more [here]().

    ```csharp
    using System.Collections;
    using System.Collections.Generic;
    using RosMessageTypes.NiryoMoveit;                  // Generated messages
    using Unity.Robotics.MessageVisualizers;            // Message visualizations
    using Unity.Robotics.ROSTCPConnector.ROSGeometry;   // Coordinate space conversions
    using Unity.Robotics.UrdfImporter;                  // URDF classes
    using UnityEngine;

    public class NiryoMoveitJointsVisualizer : DrawingVisualizer<NiryoMoveitJointsMsg>
    {
        // Start is called before the first frame update
        void Start()
        ...
    }
    ```

    Your template class should now look like the above code block. Next, we'll add the GUI window to

### Drawing the UI Window

### Adding Customization Parameters

### Drawing a Pose

TODO: repeat process with Place Pose

### Drawing a Robot

## More with Message Visualizations

You can proceed to the next tutorial, [TEMP link] [Visualizing Custom Services]().

To learn more about using the Message Visualizations package, visit the package [TEMP link] [documentation](https://github.com/Unity-Technologies/ROS-TCP-Connector/blob/amanda/default-tutorial/com.unity.robotics.message-visualizations/Documentation~/README.md).