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
```
---
