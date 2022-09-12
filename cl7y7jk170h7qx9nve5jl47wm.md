## Singleton Design Pattern

### Introduction

The singleton pattern is one of the **simplest design patterns**.The singleton pattern is a design pattern that **restricts the instantiation** of a class to one object.

Singleton is a **creational design pattern** that lets you ensure that a class has only one instance, while providing a **global access point to this instance**.

### Example

1. **Simple deck of cards**
When most of us sit down to play a few games of poker with our buddies, we often play using a single entity known as the deck. This typically consists of 52 cards in total, made up of thirteen ranks of four suits each. When a hand is dealt around the table, all cards are obtained from that single shuffled instance of the deck. Once the hand is over and you’ve (hopefully) taken your friends for all they’re worth, all 52 cards are gathered up and shuffled back into that same single instance of the deck, then a new hand is dealt from it. Repeat ad nauseam until all money is lost and/or drunkenness overtakes you.

2. **Government**
Government is a single entity. We can refer as Currently its the “Governement of X “. Value of X ( Ministers ) may change but still its the same Government.

### When not to use this Pattern ?

Whenever your class is dealing with some specific identifier to the objects, at that time we should not use this pattern. Example, Consider the **Student** class, where there will be a unique **roll_num** for a individual students. During this scenario we should not use the singleton Pattern.

### When to use this Pattern ?
Whenever we are creating a class to share the common values , at that scenario we can use this kind of pattern.

### Implementation

#### Method 1
%[https://gist.github.com/syedjafer/010caf3f4eb59ab35aa02365629d2a5c#file-method_2_singleton-py]

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662565922156/CjU9zYgp-.png align="left")

#### Method 2
%[https://gist.github.com/syedjafer/2f9499f95f70275b17ef8336c9e0677e#file-method_1_singleton-py]

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1662566060208/qmTA0ZERo.png align="left")


### Final Thoughts
Though singleton pattern helps us in many scenarios; it's defined as an evil design pattern in DDD (Domain Driven Design) designing system. We will further discuss about this drawback in upcoming post. 
