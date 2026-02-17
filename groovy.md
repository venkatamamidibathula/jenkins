# Groovy 


```groovy

def x = 5

x +=5

println x

assert x == 10: "Value should be ten"


String name = "Mahesh Mamidibathula"

int coursecount = 14

BigDecimal salary = 999999.99999

Boolean isProgrammer = true


println name + "has created" + coursecount + " courses ."

println name + " is a programmer ?" + isProgrammer.toString().capitalize()

println name + "wishes his salary was \$" + salary


String[] users = ["Mahesh", "Mike", "John"]

println("-----------------")
for (String singer:users){
    println singer
 }

println("--------------------")
users.each {println it}

println("--------------------")

int i=0
for (;i<coursecount;i++){

    println (i)
    
 }
 
 println("-----------")
 while (i<coursecount){
     println(i)
     i++
 }
 


```


**Generating userid from firstnames and last names**

```groovy


String getusername(String firstname, String lastname){

    return firstname.substring(0,1).toLowerCase() + lastname.toLowerCase()

}
 
 
assert getusername("Chris","Barn") == "cbarn" : "getusername is not working"

void printcredential(cred){

    println("Username is ${cred}");
 
 }
 
 
 printcredential(getusername("Chris","Barn"));
 
 
String[] firstnames = ["MAHESH", "Mike", "Jake", "Lime"]
String[] lastnames = ["Mamidibathula","Drake", "Jessy", "Virginia"]

for (int i=0; i < firstnames.size(); i++) {
    printcredential(getusername(firstnames[i], lastnames[i]))
}


```


---

# Classes and Objects


Generating userid's using class and objects


```groovy

class User {

    String firstname;
    String lastname;
    
    public String username(){
    
        return getusername(this.firstname, this.lastname);
        
    }
    
    private String getusername(String firstname, String lastname){
        return firstname.toLowerCase().substring(0,1)+lastname.toLowerCase();
    }
  
  }
  
  
  User [] users = [new User(firstname: "Bob" , lastname: "Dylan"), new User(firstname: "Jeff", lastname: "Nelson"), new User(firstname: "Liam", lastname: "Nesson")];
  
  users.each(user -> println("Username is ${user.username()}"));


```
