# Go Structs 
### Structs 
- also called as structure 
- user defined type (composite in nature)
- allows to group/combine items of possibly different types into a single  type. 
- can represent real-world entity which has some set of properties/fields 
- compared as a classes in object-oriented programming.
- termed as a lightweight class that doesnot support inheritance but supports composition
```go 
type Address struct {
  name string 
  street string 
  city string 
  state string 
  Pincode int 
}
```
The above code can be made compact by combining the various fields of the same type. 
```go 
type Address struct {
    name, street, city, state string
    Pincode int
}
```
- Syntax for declaring structure `var a Address` 
- variable of a type Address which is by default set to zero. 
- by default in a struct all the fields are set to their corresponding zero values ( text to "", int to 0).
- structs can also be initalized through struct literals like `var a = Address{"A","B","C","D"}`

```go
// declare and define the struct 
package main 
import "fmt"

// defining a struct type 
type Address struct {
  Name string
  city string 
  Pincode int 
}
func main(){
  // Declaring a variable of struct type 
  // All the striuct fields are initalized 
  // with their zero value
  var a Address
  fmt.Println(a)
  
  // Declaring and initalising a 
  // struct using struct literal 
  a1 := Address{"A","B",1234}
  fmt.Ptintln{"A",a1}
  
  // naming fields while 
  // initalizing a struct 
  a2 := Address{Name:"A",city:"C",Pincode:12345}
  fmt.Println("Address2",a2)
  
  // uninitalized fields are set to 
  // their corresponding zero-value
  a3 := Address{Name:"B"}
  fmt.Println("Address3:",a3)
  
}
/*
Output:
{0}
Address1: {A B 1234}
Address2: {A C 12345}
Address3: {B 0}
*/
````
---
### Access fields of a struct 
- by use of dot (.) operator
```go
// access the fields of struct 
package main
import "fmt"

// defining the struct 
type Car struct {
  Name,Model,Color string 
  WeightinKg float64
  }

// Main function 
func main() {
   c := Car{Name:"A",Model:"Xc1",Color:"Red",WeightInKg:1920}
   // Accessing the struct fields 
   // using the dot operator 
   fmt.Println("Car Name:",c.Name)
   fmt.Println("Car Color",c.Color)
   
   // Assigning a new value
   // to a struct field
   c.Color = "Black"
   
   // Displaying the result 
   fmt.Println("Car",c)
}
/*
Output
Car Name: A 
Car Color: Red 
Car: {A Xc1 Black 1920}
*/
````
---
### Pointer to a struct 
- pointers are a variable which is used to store the memory address of another variable.
```go 
// pointer to struct 
package main
import "fmt"

// defining a structure 
type Employee struct {
    firstName,lastName string
    age, salary int 
}

func main() {
  // passing the address of stuct variable 
  // emp is a pointer to the Employee struct 
  
  emp := Employee{"A","B",55,600}
  
  // (*emp).fistName is the syntax to access 
  // the firstName field of the emp struct 
  
  fmt.Println("First Name: ",(*emp).firstName)
  fmt.Println("Age;",(*emp).age)  
}
/*
Ouptput
First Name: A
Age: 55
*/

// pointer to struct 
package main
import "fmt"

// defining a structure 
type Employee struct {
    firstName,lastName string
    age, salary int 
}

func main() {
  // passing the address of stuct variable 
  // emp is a pointer to the Employee struct 
  
  emp := &Employee{"A","B",55,600}
  
  // (*emp).fistName is the syntax to access 
  // the firstName field of the emp struct 
  
  fmt.Println("First Name: ",emp.firstName)
  fmt.Println("Age;",emp.age)  
}
/*
Ouptput
First Name: A
Age: 55
*/
```
---
### Struct Comparision 
- comparision of two structs are allowed if they are of the same type and contain the same fields values with the help of == operator or DeeplyEqual() method. 
- Both the operator and method return true if the structures are identically equal else return false. 
```go 
// using == operator 
package main
import "fmt"

// Creating a structure 
type Author struct {
  name string
  branch string 
  language string 
  Particles int 
}
// Main function 
func main(){
  // Creating variables
  a1 := Author{
    name: "A",
    branch: "B",
    language: "C",
    Particles: 12,
  }
  a2 := Author{
    name: "C",
    branch: "D",
    language: "E",
    Particles: 13,
  }
  a3 := Author{
    name: "F",
    branch: "G",
    language: "H",
    Particles: 14,
  }
  // Checking if a1 is equal 
  // to a2 or not 
  // using == operator 
  if a1 == a2 {
    fmt.Println("Variable a1 is equal to variable a2")
  } else {
    fmt.Println("Variable a1 is not equal to varaible at a2")
  }
  
  // Checking if a1 is equal
  // to a2 or not 
  // using == operator 
  if a2 == a3 {
    fmt.Println("Variable a2 is equal to variable a3")
   } else {
     fmt.Println("Variable a2 is not equal to variable a3")
   }
 }
 /*
 Output:
 Variable a1 is equal to varaible a2
 Varaible a2 is not equal to variables a3
 */
 

// using DeepEqual() method
package main

import (
	"fmt"
	"reflect"
)

// Creating a structure
type Author struct {
	name	 string
	branch string
	language string
	Particles int
}

// Main function
func main() {

	// Creating variables
	// of Author structure
	a1 := Author{
		name:	 "S",
		branch: "C",
		language: "P",
		Particles: 48,
	}

	a2 := Author{
		name:	 "S1",
		branch: "C1",
		language: "P1",
		Particles: 78,
	}

	a3 := Author{
		name:	 "D",
		branch: "C2",
		language: "P2",
		Particles: 88,
	}
	
	// Compairing a1 with a2
	// Using DeepEqual() method
	fmt.Println("Is a1 equal to a2: ", reflect.DeepEqual(a1, a2))

	// Compairing a2 with a3
	// Using DeepEqual() method
	fmt.Println("Is a2 equal to a3: ", reflect.DeepEqual(a2, a3))
}
/*
Output
Is a1 equal to a2:  true
Is a2 equal to a3:  false
*/
````
