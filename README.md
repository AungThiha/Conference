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


### Requirements
* Python 2.7
* Google App Engine SDK for Python
* Git
* Terminal or command prompt


### How to download
Open up your terminal or command prompt and enter the following command to download
* $ git clone git@github.com:AungThiha/Conference.git


### How To run the application
Open up your terminal or command prompt and run the command below:<br>
* $ dev_appserver.py .


### Task 1: Add Sessions to a Conference

#### Explain your design choices
I created session model with the following datastore properties:
```
class Session(ndb.Model):
    """Session -- Session object"""
    name = ndb.StringProperty(required=True)
    highlights = ndb.StringProperty()
    speaker = ndb.StringProperty(required=True)
    duration = ndb.IntegerProperty()
    typeOfSession = ndb.StringProperty(repeated=True)
    date = ndb.DateProperty()
    startTime = ndb.TimeProperty()
```
* Since a session without a name and a speaker wouldn't make sense, I implemented **name** and **speaker** as **required** fields.<br>
* **Speaker** is defined as a **String** property to avoid the need to create a separate speaker entity/kind.<br>
* **Duration** is better to be saved in Integer Value, so that we do not need to type cast when we need to make some calculation with it.
So, I implemented **duration** as **Integer** property.<br>
* Session may belong to many types. For example, a session about *Python* belongs to two types that are *Technology* and *Programming Languages*.
So, I implemented **typeOfSession** as **repeated** property.


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