# Image-Based-Visual-Servoing-Tutorial
This repository is a resource for anyone interested in implementing the basics of image-based visual servoing methods . With the help of the included scripts and files, you'll be able to quickly create an implementation.

## Implementation
### Prerequirest
The Gazebo simulation environment and the ROS environment and the integration of these two are required to use this method. (Used ROS version: Noetic, Gazebo version:1.12)

You can use the following link to install these:https://classic.gazebosim.org/tutorials?tut=install_ubuntu

After the installation build you can build the 'pack' package and use that.

### Using the package

Starting roscore to use ROS communication:

    roscore

Launch the Gazebo world file:

    roslaunch pack launcher.launch
    
Setup a topic to adjust camera position:

    rosrun pack Set_camera_position_from_topic.py
    
Set the camera position to the hard coded coordinates, this position will be the desired position:

    rosrun pack Publish_camera_position_to_topic.py
    
Create desired input values (image,Z value):

    rosrun pack Feature_image.py
    
Change hard coded camera position in Publish_camera_position_to_topic.py to the starting position, and then rerun that. 

    rosrun pack Publish_camera_position_to_topic.py
    
Start image based visual servoing method:

    rosrun pack IBVS.py
    
## Example

Running the following commands in separated command windows:

    roscore
    roslaunch pack launcher.launch
    rosrun pack Set_camera_position_from_topic.py
    
Define the coordinates in Publish_camera_position_to_topic.py

    if __name__ == '__main__':
    values = np.array([0,0,0.3,180,0,0]) # desired camera position for now
    publish_camera_pose(values)

Create desired input values (image,Z value):

    rosrun pack Feature_image.py
    
Define the coordinates in Publish_camera_position_to_topic.py

    if __name__ == '__main__':
    values = np.array([0.015,-0.01,0.5,179,2,30]) #starting camera position
    publish_camera_pose(values)
    
Start image based visual servoing method:

    rosrun pack IBVS.py
    
The moving of the camera object can be seen on the Gazebo simulation window, and the error vector can be seen on the commander:
![](https://i.imgur.com/kThQWK7.jpg)

![](https://i.imgur.com/9v7HmLq.jpg)

![](https://i.imgur.com/XCJuzJG.jpg)

![](https://i.imgur.com/cIjHVzi.jpg)

![](https://i.imgur.com/bsFwcOi.jpg)

![](https://i.imgur.com/Z9dgrse.jpg)

![](https://i.imgur.com/oV1SVRw.jpg)

![](https://i.imgur.com/ESXqDXa.jpg)

The camera position during the method: 

![](https://i.imgur.com/eHNBvPn.png)


