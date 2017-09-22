# Tools to steal ROS messages definitions
Ever been in the situation you had a robot that you could access but
your computer didn't have the proper messages installed/compiled for that specific robot. And sometimes you don't even know the version it's using
so you feel even more hopeless?

I got you covered!

Here you can find some utilities that may help you. Or at least they were fun to tinker with and are useful to me.

They create a workspace with fake packages that contain the message definitions that were found, compile, source and talk to the robot!

* `get_all_runtime_msgs.py`: If you have ssh access to the robot (and you know which workspace to source too, maybe), you can copy this script into it and execute it. It will create for you a _catkin_ws_ with generated packages faking all the ones that are needed to communicate with the current published topics, services and action servers. In a handy gzip file. Just copy to your machine, extract, `catkin_make` and source, and you are good to go.
* `make_ws_from_all_publishers.py`: Run it and it will build a _catkin_ws_ with all the messages from the topics that have a publisher to steal the message definition from.
* `steal_msg_from_pub.py`: You only got network access? Well, if there is a topic publisher of a message you are interested, just run this tool and it will steal for you the message definition of that topic. What can you do with that? See next tool!
* `recreate_msgs.py`: Given a message definition it creates a _catkin_ws_ with fake packages that create all the necessary messages to talk to that topic. You don't even need `std_msgs`!
* `make_ws_from_topic_publisher.py`: Give it a topic with a publisher and it will build a workspace for you to be able to echo/pub into it.

TODO: Add stealing of all current python compiled messages in a thing that allows you to use it instantanously.
