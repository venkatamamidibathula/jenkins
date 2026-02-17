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

