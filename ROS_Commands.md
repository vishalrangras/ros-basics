	
	Sourcing ROS Environment:
	
		Each ROS Distribution provides a handy little script called setup.bash, specifically to source the environment (i.e. environment variables). To run the script, following command can be executed:
		
			source /opt/ros/kinetic/setup.bash
			
		The Environment variables tell our bash shell where ROS Commands and packages can be found. To verify if the environment is sourced properly to BASH Shell or not, you can use tab completion feature with any ROS command, e.g.: ros /tab/tab
		
		To permanently source the environment to .bashrc, following command should be executed. This will ensure that we don't have to source it every time we open the new terminal.
		
			echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
			
		
		
	ROS Commands
		
		
		roscore - To start the master process of ROS
		rosrun <<package_name>> <<node_name>> - To run a particular node of a given package
		
		rosnode list - To list all the running nodes
		
		rostopic list - To list all the available topics (Consider these as channels / pipe in EIP Analogy)
		rostopic info <<name_of_topic>> - To get more details like publishers and subscribers of a topic, type of topic.
		
		rosmsg show <<message_type_name>> - To get more information about a particular topic.
		rosed <<package_name>> <<file_name>> - Allows you to easily view and edit files in your ros environment.
		
		rostopic echo <<name_of_topic>> - Allows you to look at the messages as they are published to a topic.
		
		roslaunch <<package_name>> <<launch_file_name>> - Allows you to launch multiple nodes with one simple command, set default parameters in the param server, automatically respond processes that have died and more.
		
	Note: After launching the master node, you can run your other nodes using rosrun command.
	
	Example:
	
		roslaunch simple_arm robot_spawn.launch
		
		source devel/setup.bash
		
		rosrun simple_arm simple_mover
		
	----------------------------------------------------------------------------------------------------------------------------------	
		
		
		rosdep check <<package_name>> - The rosdep tool will check for a package missing dependencies, download them and install them.
		
		rosdep install -i <<package_name>> - To install all the missing dependencies of a given package.
		
		To Create Catkin Workspace:
		
			$ mkdir -p ~/catkin_ws/src
			
			$ cd ~/catkin_ws/src
			
			$ catkin_init_workspace
			
			$ cd ~/catkin_ws
			
			$ catkin_make
			
		To create a package:
		
			catkin_create_pkg <<pkg_name>> [dependency_1 dependency_2 ...]
			
			
			
	Some ROSPY Syntax:
	
		service = rospy.Service('service_name', serviceClassName, handler)
		
		service_proxy = rospy.ServiceProxy('service_name', serviceClassName)
		
		