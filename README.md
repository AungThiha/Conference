# Conference
Full-Stack Web Nanodegree ( Project 4 )

The project is a conference organization app.<br>
The project consists of:<br>
* Setting up database
* CRUD operation
* User profiles
* Conference information
* Session information
* User's Wishlist
* Implementing API end points
* Authentication and authorization

The app is deployed on google cloud platform at https://conference-1151.appspot.com/


### Task 1: Add Sessions to a Conference

#### Explain your design choices
Speaker is defined as a StringProperty to avoid the need create a separate speaker entity.


### Task 3: Work on indexes and queries

#### Come up with 2 additional queries
Say user would like to attend session when he/she free 
and he/she would be free only after a specific time, 
so he/she would like to check which sessions he/she can catch up with. 
In that case, I've implemented **getSessionsAfter**.

Another query is that in case user would like to know who is attending
the conference, I've implemented **getAttenders**.

#### Solve the following query related problem
Question: Let’s say that you don't like workshops and you don't like sessions after 7 pm. How would you handle a query for all non-workshop sessions before 7 pm? What is the problem for implementing this query? What ways to solve it did you think of?

Answer: Datastore has a limitation that it can not be used two inequality filters when query. One way to solve this is to query sessions before 7pm first and then filter it out in python code to remove sessions with a 'workshop' type.