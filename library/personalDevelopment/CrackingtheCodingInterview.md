# Cracking the Coding Interview
__By: Gayle Laakmann McDowell__
## Lessons Learned: 
- Optimize code by looking for BUD (bottlenecks, unnecessary work, and duplicated work)
- Vertical scaling means increasing the resources of a specific node, for example adding more ram to a sever. Horizontal scaling is adding more nodes, for example adding more servers.
- An in memory cache can deliver results super quick. It is a simple key-value pair that typically sits between your application and your data store. When an application requests a piece of information, it first tries the cache. If the cache does not contain the key, if will look up the data in storage. When you cache, you might cache a query and it’s results directly
- Asynchronous programming is a form of parallel programming that allows a unit of work to run separately from the primary application thread
- Pre-processesing should also be considered as you can run some things and store them in memory before the user starts working on things
- Networking metrics: bandwidth (maximum amount of data that can be transferred in a unit of time, bits per second), throughput (the actual amount of data that is transferred, bandwidth is the max), and latency (how long it takes data to go from one end to the other, the delay between sender sending data and the receiver receiving it)
- Testing questions usually fall under one of four categories: 1. Test a real world object like a pen 2. Test a piece of software 3. Write test code for a function 4. Troubleshoot an existing issue
- In black box testing we are just given the software as is and need to test it. In white box testing we have additional programmatic access to test individual functions inside the code
- Overloading in Java is when two methods have the same name but differ in the type or number of arguments
- Overriding in Java is when a method shares the same name as another method in its super class. For example, you can have a class named shape that has a method that computes area and you can have a circle class that extends the shape class and has its own method that computes area. In this example the circle class method overrides the shape class method
- System design questions, step by step. 1. Scope the problem 2. Make reasonable assumptions and communicate them 3. Draw the major components out 4. Identify the key issues 5. Redesign for the key issues
- Depth-first search utilizes recursion to look through each branch. Breath-first search does not use recursion, but instead utilizes a queue
- A binary search tree is a binary tree in which every node fits a specific ordering property: all left descendants < n < right descendants
- Binary tree is a tree in which each node has up to two children
- Do error checking. Don’t assume the input, instead validate the input is what it should be. Example would be an if statement at the beginning to check the input. Don’t do this too much, but if you don’t write it out in the interview, you should at least make a comment that you would do an error check in certain places.
- Writing flexible, general purpose code may mean using variables instead of hard coding values. If we can write our code to solve a more general problem, we should. This solution is much more complex for the general case.
- When you get a question, try working it through on a real world example. For example, if you are given an alphabetized list of names and need to go to Kendra, you wouldn’t start from the start, you would jump to the middle and go from there.
- You can do a conceptual test of your code by reading and analyzing what each line of code does. Think about if it does what you think it should do
- Steps to solve a problem: 1. Listen carefully 2. Draw an example 3. State a brute force 4. Optimize 5. Walk through 6. Implement 7. Test
- Concepts to know: bit manipulation, memory (stacks vs heaps), recursion, dynamic programming, big O time and space
- Algorithms to know: breadth-first search, depth-first search, binary search, merge sort, quick sort
- Core data structures to know: linked lists, trees, tries, graphs, heaps, vectors or arraylists, hash tables
- If a recursion function is called twice within a recursion function, then it is O(2^N). Similarly, if a recursion function is called three times within a recursion function, then it is O(3^N)
- When answering interview questions, use the SAR method. Situation, action, result
- Resume bullet points should show what you did, how you did it, and what the results were. Ideally these would be measurable
- You should do your best to talk out loud throughout the problem and explain your thought process. The interviewer is most interested in your thought process and how you go about solving the problem