# Chapter 3: The Digital Twin (Gazebo & Unity)

**TL;DR:** Digital twins simulate robots in virtual environments, allowing safe testing and visualization before deploying to physical robots.

## Learning Objectives
- Build and simulate robots in Gazebo.  
- Understand URDF (Unified Robot Description Format) and SDF formats.  
- Implement sensors and detect collisions.  
- Render humanoid robots in Unity for high-fidelity visualization.

## Content
A **digital twin** is a virtual replica of a physical robot and its environment. It allows developers to:
- Test algorithms safely.  
- Tune robot parameters before real-world deployment.  
- Visualize sensors and actuators without hardware.  

**Gazebo** simulates physics, gravity, and collisions. Sensors like LIDAR, cameras, and IMUs can be emulated.  
**Unity** provides realistic rendering and human-robot interaction simulation, including lighting, textures, and animations.

### Example URDF snippet for a LiDAR sensor
```xml
<sensor name="lidar_sensor" type="ray">
  <ray>
    <scan>
      <horizontal>
        <samples>640</samples>
        <resolution>1</resolution>
        <min_angle>-1.57</min_angle>
        <max_angle>1.57</max_angle>
      </horizontal>
    </scan>
    <range>
      <min>0.2</min>
      <max>10</max>
    </range>
  </ray>
</sensor>
