# DS Homework 1 - README
## Lau Yu Hui 1004410

### General
For most of the code, merely run the `main.go` via `go run main.go` of the appropriately labelled folder. For example, to run the code for question 2.1, just run the `main.go` inside the folder **question2.1**. 

The only places where editing of the main code directly is necessary when the questions have multiple parts like questions **2.1 and 2.2**.

#### Question 2.1
 To demonstrate the two cases, edit the *scenario()* function around line 74. As written in the comments, by changing the **finder**, you can change the scenario in which you're running. 
 
 If you want to run the **best** case scenario, uncomment `finder := NUM_CLIENT - 2` along with the accompanied print statement.
 
For **worst** case scenario, uncomment  `finder := 0` and the accompanied print statement.

![2 1func](https://user-images.githubusercontent.com/56100464/156935166-8effda69-16a3-4bfa-8191-3dfb44ce135e.png)

#### Question 2.2
To alternate between scenarios **a** & **b**, merely change the input at line 276.

- Scenario **a** - 1
- Scenario **b** - 2

![2 2func](https://user-images.githubusercontent.com/56100464/156935200-959ba5d5-e82f-4faa-85c8-272c6d90b19b.png)

--- 

### Output 
The following sections will be a brief summary on how to interpret the outputs of the respective questions.

#### Question 1

#### Question 1.1
Simple program demostrating different goroutines receiving messages from each other. With the number on the left representing the recipient and the number on the right representing the sender.

![1 1](https://user-images.githubusercontent.com/56100464/156935211-a0e862d7-8556-4365-8a5c-62eff22e1369.png)


#### Question 1.2
The image below shows the interaction between the various goroutines, similar to that of 1.1

![1 2 1](https://user-images.githubusercontent.com/56100464/156935217-f0f99ea8-411b-40a8-a446-2d8c350dd3f5.png)


This is the total order of the interactions shown in the above screenshots, arranged according to the logical clock. If they have the same logical clock, they are then arranged in ascending numbers of their PIDs.

The actions and respective process clocks are also recorded under their respective columns.
![1 2 2](https://user-images.githubusercontent.com/56100464/156935220-1590aedd-9691-455a-8ec4-bc40a6c7449f.png)

#### Question 1.3

Similar to that of 1.1 and 1.2, however, this time the timings are recorded in a vector clock format. At the end of the program, each goroutine will send out if it managed to record any violation during the program.

![1 3 2](https://user-images.githubusercontent.com/56100464/156935231-ce5d3106-8850-4b31-9465-72b96190cf92.png)

#### Question 2

#### Question 2.1
##### Best

As you can see from the image above, **8**, the node with the second largest ID, is the first one to notice after the coordinator **9** breaks down.

![2 1 2-best](https://user-images.githubusercontent.com/56100464/156935247-dcf61617-bc48-4de3-8075-32a9b97b12ee.png)


The next coordinator check shows that **8** is indeed the new coordinator but this changes when **9** wakes up and starts an election.
##### Worst

![2 1 1-worst](https://user-images.githubusercontent.com/56100464/156935252-e10e7dc1-3178-4ea2-af10-3f0848fdb809.png)

Similar to that of the best case but in this case, **0**, the node with the smallest ID, is first to notice that **9** has broken down. We see that a cascade of elections start in the order of their IDs which represents the most time consuming scenario where every node holds an election. 

![2 1 2-worst](https://user-images.githubusercontent.com/56100464/156935255-86795d8f-5206-4971-9e8f-7778d128213d.png)

At the end, **8** wins the election, like in the best case but this takes longer.  

##### Question 2.2
##### Newly elected coordinator fails while announcing win

![2 2 a](https://user-images.githubusercontent.com/56100464/156935261-fc088fb9-988a-45fd-a541-3c5ae65a99a8.png)

We see that Node **3** starts an election when it realises that **4** has broken down but it only manages to notify node **0** before it breaks down. As a result, during the coordinator check, only nodes **3 and 0** have **3** has their coordinator while the rest still thinks of **4** as their coordinator.

##### Failed node is not the newly elected coordinator

![2 2 b](https://user-images.githubusercontent.com/56100464/156935266-07227219-d573-4b10-b713-be423f97c6ea.png)

Node **2** fails while **3** is annoucing it's win, hence Node **2** did not receive the update information and thinks that **4** is still its coordinator.

#### Question 2.3

![2 3](https://user-images.githubusercontent.com/56100464/156935268-fd6af09f-7841-4b8d-86a0-fe0ee2f0955b.png)

For this question, the nodes that send the message to the coordinator after it breaks down is randomnized. We see that for this case, **0** and **3** contact **5** upon its failure and start elections respectively. This starts off a few elections until **4** finally ends up as the coordinator. (Only **5** did not get the new coordinator message as it is still down)

#### Question 2.4

![2 4](https://user-images.githubusercontent.com/56100464/156935271-aca08fcd-7f6a-4bf4-b27b-35355d0bb22d.png)

We see that **10** joins the network after the other nodes and starts a new election upon it joining. Since **10** is now the node with the largest ID, it becomes the new coordinator.

