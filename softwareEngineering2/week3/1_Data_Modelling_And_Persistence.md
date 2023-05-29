# Data Modelling and Persistence
![[Pasted image 20230530003852.png]]
* Spring sets up database tables through the use of converting java classes into database models and modelling relationships with annotations in the code.
* The service interfaces allows for finer grained data manipulation before passing it to the controller outside of the query layer that the repository handles.
* The repository layer deals with the querying of the data from the database and provides built in methods for doing so.