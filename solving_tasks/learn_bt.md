# Understanding Behavior Trees and how to effectively use them

For 2025 (and onwards) our task solving system is going to be based around behavior tree, in order to implement them one needs to be aware of how they work.

This guide is not self complete, one must first understand the nuances of using actions which can be achieved by following the ROS action guide.

## Starter guide

[this small article](https://medium.com/@nullbyte.in/behavior-trees-for-ros2-part-1-unlocking-advanced-robotic-decision-making-and-control-7856582fb812
) is a pretty good starting guide on how to setup a tree and how they work as far as their coding go. This guide is not for the library we're using so things will look slightly different.

## Additional information

### Understanding the theory and abstraction system

[There is a book](https://arxiv.org/abs/1709.00084) which is essentially what was used as a guide for the article (even the images used in the article come from here). Obviously I don't expect you to read it all, however, I did, so here's a guide on what is useful.

- **Chapter 1.3 to 1.5**: They present a guide on how to perform abstraction from a behavior tree to code and vice-versa, followed by examples on how to build a tree to perform a task. After that the chapter contains a few less fleshed out examples.

- **Chapter 2.1**: People migrating state machines used in 2024 might find this useful since it essentially contains a guide on how to do exactly that. Remember that State machines are bad at reactivity so writing from scratch might be adviseable.

- **Chapter 2.6**: Just advantages and disadvantages (especially important if one is considering changing our system to another task orchestration method)

- **Chapter 3**: Design priciples, mainly ideas to follow for good designing. Most of them are obvious, but try to read at least 3.1, 3.2 and 3.4

### Understanding the library behaviortree_cpp_v3

As far as I'm aware there is no official documentation outside the source code, however, this library is the only one that is actively developed and doesn't have glaring issues opened like 2 years ago.

[Here's the code](https://github.com/BehaviorTree/behaviortree_cpp_v3-release). To make sense of it go to upstream repositories and have a look at the code. Most of the useful implementation information is present in `include/behaviortree_cpp`, especifically the .h not inside folders. For example, `action_node.h` contains declarations for all possible sync and async use cases presented and their use cases.

My suggestion: services and quick synchronous action (aka waiting for the response instead of returning running) should use `SimpleActionNode`. Long running actions which would stop the tree for too long and lose reactivity should use `StatefulActionNode`. Nodes which communicate to a system external to ROS should use `CoroActionNode` (or Stateful in case the additions to Coro are not necessary).

I still have to create a video creating those nodes on a real enviroment.

### Future considerations and developments

[Back to the book](https://arxiv.org/abs/1709.00084).

- **Chapter 7.1**: Planning and acting approach. Essentially you give the system a goal and it builds a tree for you, looking to achieve said goal. The chapter goes into some detail, however, when actually building the system it might be helpful to look at the references. As far as I understand the system uses no simulation to build a tree iteratively.

- **Chapter 7.2**: This might be a good idea on what to move into if we feel planning and acting is insufficinent, it would take a lot of effort though. It is essentially a language for task planning which can output BT.

- **Chapter 8**: (8.2 if you know what genetiv algorithms are) They use machine learning and simulations in order to build a behavior tree, adjusting fitness metrics for a complex system such as apollo, zeus or bellator might be a problem due to the complexity.
