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
