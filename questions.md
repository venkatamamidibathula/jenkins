1. Write a groovy scipt to generate domain id based on first names and last names lists?
String[] firstnames = ["MAHESH", "Mike", "Jake", "Lime"]
String[] lastnames = ["Mamidibathula","Drake", "Jessy", "Virginia"]

```groovy


String getusername(String firstname, String lastname){

    return firstname.substring(0,1).toLowerCase() + lastname.toLowerCase()

}
 
 
assert getusername("Chris","Barn") == "cbarn" : "getusername is not working"

void printcredential(cred){

    println("Username is ${cred}");
 
 }
 
 
 
String[] firstnames = ["MAHESH", "Mike", "Jake", "Lime"]
String[] lastnames = ["Mamidibathula","Drake", "Jessy", "Virginia"]

for (int i=0; i < firstnames.size(); i++) {
    printcredential(getusername(firstnames[i], lastnames[i]))
}


```

2. Write a groovy scipt in terms of classes and objects?


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

3. Write a groovy script in terms of abstract classes where user is abstracted for artist and producer?

```groovy



class RegularUser extends User { }
abstract class User {
    String firstname
    String lastname
    
    public String username() {
        return getusername(firstname, lastname)
    }
    
    private String getusername(String firstname, String lastname) {
        return firstname.toLowerCase().substring(0,1) + lastname.toLowerCase()
    }
}



class Artist extends User {
    public String[] Songs;
}

class Producer extends User {
    public void Produce() {
        println("Album Complete")
    }
}

User[] users = [new RegularUser(firstname: "Bob", lastname: "Dylan"),new RegularUser(firstname: "Jeff", lastname: "Nelson"), new RegularUser(firstname: "Liam", lastname: "Nesson"),new Artist(firstname: "Roy", lastname: "Wilson", Songs: ["BEkhayalo","Sadma"]),new Producer(firstname: "Satyajit", lastname: "Ray")];

users.each { user -> 
    if (user instanceof Artist) {              
        println("Username is ${user.username()}") 
        user.Songs.each { song -> println("${song}") }
    } else if (user instanceof Producer) { 
        user.Produce()
    } else {
        println("${user.username()} - Regular user") 
    }
}


```
