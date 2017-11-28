## Scala Basics Exercise

### Option

Write a _CarService_ , that returns an object of the type _Car_ by a _CarID_.
Request a couple of cars by calling the service method _getCarByID_ and calculate the average price of all used cars.
Consider that the CarService can return Cars that are not used or even a null value, if no car with the given id exists.
Write the exercise in the first step without using the Option, use if statements to nullcheck the values instead.
Then refactor your code and use the Option type of scala.
 - Write a Car class with some Properties, e.g. id, brand, modell, registrationDate, isUsed, price, etc.
 - Write a CarService that contains a Collection of Cars and method that cretrieves a car by its ID. If no car is found for the                given ID, it should return _null_
 - Fill the the CarService with some Car objects 
 - Request some cars by their IDs and also request some IDs where not car will be found
 - Calculate the average price of all used cars and avoid NullPointerExceptions without using Option type 
 - Refactor your code and use the Option type 
   
### Future
For this exercise we are using a simple JSON Server which can be acessed with
https://my-json-server.typicode.com/anfalt/MonadsInScala/. 
There is a REST Endpoint called for Customers and Invoices:
https://my-json-server.typicode.com/anfalt/MonadsInScala/Customers
https://my-json-server.typicode.com/anfalt/MonadsInScala/Invoices
First build a simple Http GET Request and wrap it in a Future. Than write a HTTPUtil class, that provides a sendGetRequestMethod.
After that request all Invoices from the REST Endpoint and calculate the average  




with the following signature: 
```scala
sendGetRequest(url: String, successCallBack: HttpResponse[String] => Unit, failureCallback: Throwable=> Unit): Unit
```

  

