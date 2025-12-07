# Chapter 1: Introduction to Physical AI

**TL;DR:** Physical AI integrates AI with the real world by giving digital intelligence a physical body.

## Learning Objectives
- Understand the concept of Physical AI.
- Explore differences between digital AI and embodied AI.
- Recognize sensors and actuators used in humanoid robotics.
- Overview the course and lab requirements.

## Content
Physical AI allows AI systems to perceive, act, and learn in the real world. Humanoid robots mirror human physical forms for seamless interaction in human environments.

**Key Sensors:**  
- LIDAR: Measures distance using lasers.  
- IMUs: Tracks orientation and balance.  
- Cameras: RGB and depth perception.

**Key Actuators:**  
- Motors and servos for movement.  
- Robotic hands for manipulation.

## Hands-on Example
```python
import rclpy
from rclpy.node import Node
from sensor_msgs.msg import Image

class CameraNode(Node):
    def __init__(self):
        super().__init__('camera_node')
        self.subscription = self.create_subscription(
            Image,
            '/camera/color/image_raw',
            self.listener_callback,
            10)
    def listener_callback(self, msg):
        self.get_logger().info('Received image frame')

rclpy.init()
node = CameraNode()
rclpy.spin(node)
