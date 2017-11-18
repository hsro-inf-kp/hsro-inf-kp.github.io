## Scala Basics 
### Option
The Option type in scala is used to wrap a value that could be null. You can compare
this type with _Nullables_ in Java. To check the value of a nullable type, you often see
nested ifs like the following:
```Java
String housenumber = null;
User user = new User();
if(user != null){
  Adress adress = user.getAdress();
  if(adress != null){
    housenumber = adress.getHousenumber();
  }
}
```
One needs to null-check every object and property of the object. You could to this
in the same way in scala. Or you could use the generic _Option_ type. An Option can
either be an instance of the _Some_ class or the _None_. As the following example shows,
the Option type provides a factory method, that creates None if the given parameter
is null, otherwise it creates an instance of Some.

```scala
val greeting: Option[String] = Some("Hello world")
val greeting2: Option[String] = None

val factoryGreeting: Option[String] = Option("Hello world")
val factoryGreeting2: Option[String] = Option(null)
```

As you can see it´s really simple to create a new Option type. By wrapping the
value that may be null with the Option, it is possible to work with it without any
null-checking.This can be achieved by using flatMap and Options.

```scala
class User(var firstName:String, var lastName:String,var address:Option[Address]){
  def getAddress():Option[Address] = return this.address
}

class Address(var city:String,var street:String,var houseNumber:Option[String]){
  def getHouseNumber():Option[String] = return this.houseNumber
}

def address1 = new Address("Rosenheim","Hochschulstr.",Option("1b"))
def address2 = new Address("Rosenheim","Hochschulstr.",Option(null))

def user1 = new User("Max","Mustermann",Option(address1))
def user2 = new User("Max","Mustermann",Option(address2))
def user3 = new User("Max","Mustermann",Option(null))

user1.getAddress().flatMap(_.getHouseNumber()) //Some(1b)
user2.getAddress().flatMap(_.getHouseNumber()) //None
user3.getAddress().flatMap(_.getHouseNumber()) //None 
```

### Future
The _Future_ type is used to run programm steps concurrently. By creating a Future it
starts running asynchronous and will return a value in some time. The _onComplete_
function accepts a callback, that gets executed, when the asynchronous function has
finished. The result value can be an instance of _Success_ or _Failure_ class, depending on whether the request was successful or not. A simple HTTP GET Request could be implemented like this.

```scala
val f = Future {
  Http("https://jsonplaceholder.typicode.com/posts/22").asString
}
f.onComplete {
  case Success(value) => println(value)
  case Failure(e) => e.printStackTrace()
}
println("This gets printed before the HTTP Response value");
```
To test this Snippet e.g in an scala worksheet, you may have to add the following line to wait until the Futere has returned a value. 
Otherwise the executing thread has stopped, before the async request has finished and now output is visible.
```scala
Await.result(f, 10 seconds)
```
Since the the future is not blocking the programm execution, the println command
gets executed before the onComplete callback. The Future type also provides a flatMap
method, that allows us to control the execution order of multiple Futures.

```scala
def getUserID() : Future[String] = {...}
def getUserAddress(userID: String) : Future[Address] = {...}
def createInvoice(address:Address) : Future[Invoice] = {...}

val futResult: Future[Invoice] =
  getUserID().flatMap( userID =>
    getUserAddress(userID).flatMap( address =>
      createInvioce(address)
    )
)
```
