## Scala Basics Exercise
### Option

1. Write a _CustomerService_ , that returns an object of the type _Customer_ by a _CustomerID_.
   Request a couple of customers by calling the service method _getCustomerByID_ and calculate the average age of all customers.
   Consider that the CustomerService can return Customers without an age or even a null value, if no customer with the given id exists.
   Write the exercise in the first step without using the Option, use if statements to nullcheck the values instead.
   Then refactor your code and use the Option type of scala.
   - Write a Customer class with some Properties, e.g. prename, surname, age, gender and customerID
   - Write a CustomerService that contains a Collection of Customers and can retrieve a customer by its ID. If no customer is found for the      given ID, it should return _null_
   - Fill the the Customer Service with some Customer objects, that 
   - Request some customers y their IDs and also request some IDs where not customer will be found
   - Calculate the average age of all customers and avoid NullPointerExceptions without using Option type
   - Refactor your code and use the Option type 
