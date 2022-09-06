## Code Smell 01 - Anemic Model / Data Clas

### Introduction

A key goal of Object Oriented design is to minimise dependencies between classes and components by packaging data and behaviour as close together as we can. In practice, a good rule of thumb for class design is to put fields and methods that use those fields in the same classes. Data classes are classes which just have fields and no behaviour (besides simple getters and setters), and they **break this rule of thumb**, creating serious dependency issues in your code.

### TL;DR:
Don't use objects as data structures. ( Class with no behaviour/functionality apart from getters and setters )

### Problems:

1. **Lack of Encapsulation** : An Anemic Domain Model always means a lack of encapsulation. You must expose invariants to external worlds. There doesn’t exist a proper way to make a former set of classes to avoid it. The classes of data end up to have no restrictions of how you can change them and therefore the responsibility to maintain the invariants shifts to the classes of operations, which is a very dangerous situation because you have to remember to keep all invariants intact each time you modify a class with data.
Lack of encapsulation leads to higher complexity, which then leads to all kinds of troubles like
  - Harder maintainability of the code 
  - Slower development
  - More bugs 
2. **Discoverability** : It can be hard to understand what the capabilities of that domain model are if it’s stripped from its behavior. That can cause code duplication because some new developers might not find a service that does the operation they need. This can be addressed by applying coding standards (project organization) so that a person knows where to expect a service class. 
3. Duplication of behaviour codes.
4. Coupling of classes.

### Explanation

Let's design a **CustomerReviewSummary** functionality, 

%[https://gist.github.com/syedjafer/76add8bc027dae6cd0f62a157e5973dd#file-anemic_model_customer_review-py]


In the above implementation of classes; the class Address and Customer are not having any behaviours. These are used as a database template or like a datastructure. All the logics were residing in the Service CustomerSummaryView. 

Let's See how it could be redesigned with DDD, RDM where the logic/behaviour would reside inside the class itself. 

%[https://gist.github.com/syedjafer/4448131a03d0fa78623bd5358558f0c7#file-ddd_model_customer_review-py]

### Solutions

1. Find Responsibilities to your class. 
2. Protect your attributes.
3. Hide implementations.
4. Delegate

There is nothing right or wrong. It's with the architect. There is an another concept called RDM (We discussed in the Explanation part). Give it a read. 


### Advantages of Anemic Model

- It’s easy to understand. Suppose you’re thinking about how you would store your data in a database. In that case, it becomes very intuitive to create a class that maps to your database schema. 
- Easy to implement. You can start quickly because you must think about the data, not the behavior right away. 

### Final Thoughts

- In Anemic Domain Models (ADM), everything happens in services. Validation, data formatting, everything.
- ADM as consisting of a set of  behaviour-free classes containing business data required to model the domain. 
- Avoid anemic models.
- Focus always on protocol/behaviour instead of data.
- Behaviour is essential, data is accidental.
- If you want to create a simple CRUD application, maybe an anemic model with a classic MVC framework is enough. But if you want to implement some kind of logic, anemic model means that you will not do object oriented programming.

### References: 

1. http://codemanship.co.uk/papers.html
2. Fowler, Martin. Anaemic Domain Model. http://www.martinfowler.com/bliki/AnemicDomainModel.html, 2003.
3. https://blog.inf.ed.ac.uk/sapm/2014/02/04/the-anaemic-domain-model-is-no-anti-pattern-its-a-solid-design/










