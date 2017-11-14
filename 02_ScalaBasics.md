##Scala Basics 
###Option
The Option type in scala is used to wrap a value that could be null. You can compare
this type with _Nullables_ in Java. To check the value of a nullable type, you often see
nested ifs like the following:
´´´java
String housenumber = null;
2 User user = new User();
3 if(user != null){
4 Adress adress = user.getAdress();
5 if(adress != null){
2
6 housenumber = adress.getHousenumber();
7 }
8 }
```
