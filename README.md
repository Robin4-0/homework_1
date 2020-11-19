# Homework 1 - Perception

Suppose to have N = 2 objects randomly placed on a table in front of a manipulator robot. They are identified by N different [APRILTAG](https://april.eecs.umich.edu/software/apriltag) markers, placed on their top. The following identification table is used:

| id | frame_id         |
| ---|:----------------:| 
| 0  | red_cube_0       |
| 1  | red_cube_1       | 
| 2  | red_cube_2       |  
| 3  | red_cube_3       |  
| 9  | blue_cube_0      |  
| 10 | blue_cube_1      |  
| 11 | blue_cube_2      |  
| 12 | blue_cube_3      |  


that means: “Apriltag with id = 0 is attached on the top of an object called red_cube_0”.

Among others, the Apriltag ROS node publishes a topic named */tag_detections*, which outputs a message of type [*geometry_msgs/PoseWithCovarianceStamped*](http://docs.ros.org/en/api/geometry_msgs/html/msg/PoseWithCovarianceStamped.html) containing the relative pose (position and orientation) between the camera frame of reference and the frame of reference of each detected tag. In this homework, the pose of the object in the camera frame of reference is called *obj_pose_camera*. 

For Homework 1 you are asked to:
- listen to the */tag_detections* topic;
- for each detected object, compute the transformation between the camera frame and the frame */world*;
- as a consequence, compute *obj_pose_world*, i.e., the pose of the tag in the frame */world*;
- publish a custom message containing [*obj_pose_camera*, *obj_pose_world*].


##### Instructions to launch the Apriltag node with 2 objects on the table:
- Open a shell and launch the simulated environment in Gazebo:
```
$ roslaunch robin_arena robin_bringup.launch simulation:=true spawn_marrtino:=false arena_name:=robin_arena_simplified
```
- Place  N = 2 objects on the white table by dragging them from the brown table.  

- On a new shell, launch the AprilTag node:
```
$ roslaunch robin_arena apriltag.launch simulation:=true
```
- Open Rviz (third shell):
```
$ rviz
```
and ADD the topic */tag_detections_image* (You can visualize the published information also by command line: rostopic echo */tag_detections* – or launching rqt_image_view and selecting the */tag_detections_image* topic)
