# Understanding Behavior Trees and how to effectively use them

For 2025 (and onwards) our task solving system is going to be based around behavior tree, in order to implement them one needs to be aware of how they work

## Starter guide

[this small article](https://medium.com/@nullbyte.in/behavior-trees-for-ros2-part-1-unlocking-advanced-robotic-decision-making-and-control-7856582fb812
) is a pretty good starting guide on how to setup a tree and how they work as far as their coding go. Actions are not defined here so this guide needs to be updated to give information on how to do a leaf node on the tree. If this has been enough for you feel free to go on your merry way.

## Additional information

### Understanding the theory and abstraction system

[There is a book](https://arxiv.org/abs/1709.00084) which is essentially what was used as a guide for the article (even the images used in the article come from here). Obviously I don't expect you to read it all, however, I did, so here's a guide on what is useful

- **Chapter 1.3 to 1.5**: They present a guide on how to perform abstraction from a behavior tree to code and vice-versa, followed by examples on how to build a tree to perform a task. After that the chapter contains a few less fleshed out examples.

- **Chapter 2.1**: People migrating state machines used in 2024 might find this useful since it essentially contains a guide on how to do exactly that. Remember that State machines are bad at reactivity so writing from scratch might be adviseable.

- **Chapter 2.6**: Just advantages and disadvantages (especially important if one is considering changing our system to another task orchestration method)

- **Chapter 3**: Design priciples, mainly ideas to follow for good designing. Most of them are obvious, but try to read at least 3.1, 3.2 and 3.4

### Understanding the library behavior_tree

[Here's the official guide](https://github.com/miccol/ROS-Behavior-Tree/blob/master/BTUserManual.pdf). Just have a look at it, most of what is mentioned here was available inside the starter guide.

### Future considerations and developments

[Back to the book](https://arxiv.org/abs/1709.00084).

- **Chapter 7.1**: Planning and acting approach. Essentially you give the system a goal and it builds a tree for you, looking to achieve said goal. The chapter goes into some detail, however, when actually building the system it might be helpful to look at the references. As far as I understand the system uses no simulation to build a tree iteratively.

- **Chapter 7.2**: This might be a good idea on what to move into if we feel planning and acting is insufficinent, it would take a lot of effort though. It is essentially a language for task planning which can output BT.

- **Chapter 8**: (8.2 if you know what genetiv algorithms are) They use machine learning and simulations in order to build a behavior tree, adjusting fitness metrics for a complex system such as apollo, zeus or bellator might be a problem due to the complexity.
