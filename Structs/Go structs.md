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
		name:	 "S",
		branch: "C",
		language: "P",
		Particles: 48,
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
---
### Nested Structure
-  A structure which is the field of another (within another) structure 
-  Synatx of Nested Structure
```go
type struct_name_1 struct{
  // Fields
} 
type struct_name_2 struct{
  variable_name  struct_name_1

}
````
- Example 
``` go 
// the nested structure
package main

import "fmt"

// Creating structure
type Student struct {
	name string
	branch string
	year int
}

// Creating nested structure
type Teacher struct {
	name string
	subject string
	exp	 int
	details Student
}

func main() {

	// Initializing the fields
	// of the structure
	result := Teacher{
		name: "A",
		subject: "Java",
		exp:	 5,
		details: Student{"B", "CSE", 2},
	}

	// Display the values
	fmt.Println("Details of the Teacher")
	fmt.Println("Teacher's name: ", result.name)
	fmt.Println("Subject: ", result.subject)
	fmt.Println("Experience: ", result.exp)

	fmt.Println("\nDetails of Student")
	fmt.Println("Student's name: ", result.details.name)
	fmt.Println("Student's branch name: ", result.details.branch)
	fmt.Println("Year: ", result.details.year)
}
/*
Output
Details of the Teacher
Teacher's name:  A
Subject:  Java
Experience:  5

Details of Student
Student's name:  B
Student's branch name:  CSE
Year:  2
*/

// Example 2 
package main
  
import "fmt"
  
// Creating structure
type Author struct {
    name   string
    branch string
    year   int
}
  
// Creating nested structure
type HR struct {
  
    // structure as a field
    details Author
}
  
func main() {
  
    // Initializing the fields
    // of the structure
    result := HR{
      
        details: Author{"S", "ECE", 2013},
    }
  
    // Display the values
    fmt.Println("\nDetails of Author")
    fmt.Println(result)
}
/*
Output:
Details of Author
{{S ECE 2013}}
*/
````
---
### Anonymous Structure 
- Anonymous Structure : A structure which does not contian name 
- useful for creation of  one time usable structure 
- Syntax :
```go 
variable_name := struct{
// fields
}{// Field_values}
````
- Example 
```go 
// Go program to illustrate the
// concept of anonymous structure
package main

import "fmt"

// Main function
func main() {

	// Creating and initializing
	// the anonymous structure
	Element := struct {
		name	 string
		branch string
		language string
		Particles int
	}{
		name:	 "A",
		branch: "ECE",
		language: "C++",
		Particles: 498,
	}

	// Display the anonymous structure
	fmt.Println(Element)
}
/*
Output 
{A ECE C++ 498}
*/
```
---
### Anonymous Fields 
- fields which do not contain any name, just simply mention the type of the fields and Go will automatically use the type as the name of the field.
- also called Embedded fields a form of Composition not inheritance.
- Syntax: 
```go 
type struct_name struct{
    int
    bool
    float64
}
````
**Important Points to remember**
- In a structure, you are not allowed to create two or more fields of the same type  (try to do so, then the compiler will give an error.)
```go 
type student struct{
int
int
}
```
- You are allowed to combine the anonymous fields with the named fields
```go 
type student struct{
 name int
 price int
 string
}
````
- Example of Anonymous Field concept
```go 
// Go program to illustrate the
// concept of anonymous structure
package main

import "fmt"

// Creating a structure
// with anonymous fields
type student struct {
	int
	string
	float64
}

// Main function
func main() {

	// Assigning values to the anonymous
	// fields of the student structure
	value := student{123, "B", 8900.23}

	// Display the values of the fields
	fmt.Println("Enrollment number : ", value.int)
	fmt.Println("Student name : ", value.string)
	fmt.Println("Package price : ", value.float64)
}
/*
Output 
Enrollment number :  123
Student name :  B
Package price :  8900.23
*/
``` 
---
### Promoted Fields  
-  are just like anonymous fields
-  the type of the field is the name of the field.
-  In "promotion”, whereby the fields or methods of embedded(anonymous) types become available on the outer/embedding(anonymous) type
-  This gives the pseudo-impression of “inheritance”, best not to think this way. 
-  Promoted fields act like ordinary fields of a struct except that they cannot be used as field names in composite literals of the struct.
- Syntax:
```go 
type x struct{
// Fields
}

type y struct{
// Fields of y structure
x
}
````
- Example 
```go 
// concept of the promoted fields
package main

import "fmt"

// Structure
type details struct {

	// Fields of the
	// details structure
	name string
	age int
	gender string
}

// Nested structure
type student struct {
	branch string
	year int
	details
}

func main() {

	// Initializing the fields of
	// the student structure
	values := student{
		branch: "CSE",
		year: 2010,
		details: details{
		
			name: "Sam",
			age: 28,
			gender: "Male",
		},
	}

	// Promoted fields of the student structure
	fmt.Println("Name: ", values.name)
	fmt.Println("Age: ", values.age)
	fmt.Println("Gender: ", values.gender)

	// Normal fields of
	// the student structure
	fmt.Println("Year: ", values.year)
	fmt.Println("Branch : ", values.branch)
}
/*
Output
Name:  Sam
Age:  28
Gender:  Male
Year:  2010
Branch :  CSE
*/
````
---
### Promoted Methods
- implemented by the child structure, and is accessible by the parent structure.
**Important Point** 
- If the child and the parent structure contain a method that has the same name but different type of receiver, then both the methods are available in the parent structure.
- If child structure contains two methods with the same name and same receiver, then these methods are not promoted in the parent structure and if you try to do, then the compiler will give an error.
```go 
// Golang program to illustrate the
// concept of the promoted methods
package main

import "fmt"

// Structure
type details struct {

	// Fields of the
	// details structure
	name string
	age	 int
	gender string
	psalary int
}

// Nested structure
type employee struct {
	post string
	eid int
	details
}

// Method
func (d details) promotmethod(tsalary int) int {
	return d.psalary * tsalary
}

func main() {

	// Initializing the fields of
	// the employee structure
	values := employee{
		post: "HR",
		eid: 4567,
		details: details{

			name: "Sam",
			age:	 28,
			gender: "Male",
			psalary: 890,
		},
	}

	// Promoted fields of the
	// employee structure
	fmt.Println("Name: ", values.name)
	fmt.Println("Age: ", values.age)
	fmt.Println("Gender: ", values.gender)
	fmt.Println("Per day salary: ", values.psalary)

	// Promoted method of the
	// employee structure
	fmt.Println("Total Salary: ", values.promotmethod(30))

	// Normal fields of
	// the employee structure
	fmt.Println("Post: ", values.post)
	fmt.Println("Employee id: ", values.eid)
}
/*
Output
Name:  Sam
Age:  28
Gender:  Male
Per day salary:  890
Total Salary:  26700
Post:  HR
Employee id:  4567
*/

// Example 2
// concept of the promoted methods
package main
import "fmt"

// Structure
type details struct {

	// Fields of the
	// details structure
	name string
	age	 int
	gender string
	psalary int
}

// Method 1
func (e employee) promotmethod(tarticle int) int {
	return e.particle * tarticle
}

// Nested structure
type employee struct {
	post	 string
	particle int
	eid	 int
	details
}

// Method 2
func (d details) promotmethod(tsalary int) int {
	return d.psalary * tsalary
}

// Main method
func main() {

	// Initializing the fields of
	// the employee structure
	values := employee{
		post:	 "HR",
		eid:	 4567,
		particle: 5,
		details: details{

			name: "Sumit",
			age:	 28,
			gender: "Male",
			psalary: 890,
		},
	}

	// Promoted fields of
	// the employee structure
	fmt.Println("Name: ", values.name)
	fmt.Println("Age: ", values.age)
	fmt.Println("Gender: ", values.gender)
	fmt.Println("Per day salary: ", values.psalary)

	// Promoted method of
	// the employee structure
	fmt.Println("Total Salary: ", values.promotmethod(30))

	// Normal fields of
	// the employee structure
	fmt.Println("Post: ", values.post)
	fmt.Println("Employee id: ", values.eid)
	fmt.Println("Total Articles: ", values.promotmethod(30))
}
/*
Output
Name:  Sam
Age:  28
Gender:  Male
Per day salary:  890
Total Salary:  150
Post:  HR
Employee id:  4567
Total Articles:  150
*/
````
---
### Function as a Field
- Syntax 
```go 
type function_name func()
type strcut_name struct{
  var_name  function_name
}
````
- Example 
```go 
// Go program to illustrate the function
// as a field in Go structure
package main

import "fmt"

// Finalsalary of function type
type Finalsalary func(int, int) int

// Creating structure
type Author struct {
	name	 string
	language string
	Marticles int
	Pay	 int

	// Function as a field
	salary Finalsalary
}

// Main method
func main() {

	// Initializing the fields
	// of the structure
	result := Author{
		name:	 "A",
		language: "Java",
		Marticles: 120,
		Pay:	 500,
		salary: func(Ma int, pay int) int {
			return Ma * pay
		},
	}

	// Display values
	fmt.Println("Author's Name: ", result.name)
	fmt.Println("Language: ", result.language)
	fmt.Println("Total number of articles published in May: ", result.Marticles)
	fmt.Println("Per article pay: ", result.Pay)
	fmt.Println("Total salary: ", result.salary(result.Marticles, result.Pay))
}
/*
Output
Author's Name:  A
Language:  Java
Total number of articles published in May:  120
Per article pay:  500
Total salary:  60000
*/

// Example 2
// as a field in Go structure
// Using anonymous function
package main

import "fmt"

// Creating structure
type Author struct {
	name	 string
	language string
	Tarticles int
	Particles int
	Pending func(int, int) int
}

// Main method
func main() {

	// Initializing the fields
	// of the structure
	result := Author{
		name:	 "A",
		language: "Java",
		Tarticles: 340,
		Particles: 259,
		Pending: func(Ta int, Pa int) int {
			return Ta - Pa
		},
	}

	// Display values
	fmt.Println("Author's Name: ", result.name)
	fmt.Println("Language: ", result.language)
	fmt.Println("Total number of articles: ", result.Tarticles)
	
	fmt.Println("Total number of published articles: ", result.Particles)
	
	fmt.Println("Pending articles: ", result.Pending(result.Tarticles, result.Particles))
}
/*
Author's Name:  A
Language:  Java
Total number of articles:  340
Total number of published articles:  259
Pending articles:  81
*/
````
----
