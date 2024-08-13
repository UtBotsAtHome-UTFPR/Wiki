# Understanding State Machines in order to use them

This is meant as a guide to find useful resources and where to look within them. Information written on guides won't be written in this file. This guide also assumes some experience on writing nodes with topics, as well as being able to make a package with executables and run your code with rosrun/roslaunch.

If information is missing contact David Segalle.

## Official documentation

The [official documentation](http://wiki.ros.org/smach/Tutorials) is a pretty good resource to begin your journey. Specifically, Learning Step-by-Step provides some insights on why the code is being designed the way it is. Learning by Example is just the examples at the end of each Step-by-Step, no need to check anything there.

SMACH Containers section has useful information as a guide of which states there are and how to use them. It is probably best to know they exist but not delve too much into it until it is needed. SMACH States contains useful information, however, not all topics are needed, Simple Action State and Service State being the only mandatory ones. We are not using actions so the only reason Action State is useful is due to shared information with Service State.

The Advanced Smach section is just a mess in general.

## A better simpler understanding

If the official documentation has left you lost in some aspect I recommend watching [this video](https://www.youtube.com/watch?v=jrV5jRs1SJc) from 23:20 forward. If even this seems incomplete look at the sidenote to see if someone has had your issue and added a simple explanation to it.

## In practice

Now, it's time to understand how all this information can be put into use on our system. Two videos are available, one on [creating services](https://www.youtube.com/watch?v=SxBXCYHSKGk) and one on [using services within a state machine context](https://youtu.be/Vh2wOgXY-kw)

## Sidenote

By default, when a service is called by a server, the server will wait until the service callback function is completed to continue, a topic will simply publish and wait. Therefore synchronous tasks are ideally made by using services and asynchronous tasks such as turning on the camera can be done by topics. Asynchronous tasks can technically be performed by changing params, however, that is bad for a multitude of reasons this guide won't get into.
