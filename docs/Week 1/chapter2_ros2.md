# Chapter 2: The Robotic Nervous System (ROS 2)

**TL;DR:** ROS 2 is middleware that connects robot components, sensors, and AI algorithms to enable humanoid control.

## Learning Objectives
- Understand ROS 2 architecture.  
- Create nodes, topics, and services in Python.  
- Connect AI agents to ROS controllers.  
- Work with URDF for humanoid description.

## Content
ROS 2 enables modular robot software. Nodes perform computations, topics handle streaming data, and services manage request/response actions.

## Hands-on Example
```python
import rclpy
from rclpy.node import Node
from std_msgs.msg import Float64

class JointPublisher(Node):
    def __init__(self):
        super().__init__('joint_pub')
        self.publisher_ = self.create_publisher(Float64, '/joint1_position_controller/command', 10)
        self.timer = self.create_timer(1.0, self.publish_joint)

    def publish_joint(self):
        msg = Float64()
        msg.data = 0.5
        self.publisher_.publish(msg)

rclpy.init()
node = JointPublisher()
rclpy.spin(node)
