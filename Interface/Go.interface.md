# Interface in Go
- Interfaces provide behavior to an object: if something can do this, then it can be used here.
- An interface defines a set of abstract methods and does not contain any variable.
- not allowed to create an instance of the interface

- syntax: 
```go 
type Namer interface {  
             Method1(param_list) return_type  
             Method2(param_list) return_type  
             ...  
}

// Example 
// Creating an interface
type myinterface interface{

// Methods
fun1() int
fun2() float64
}
````
**Implementing of interfaces**
- it is necessary to implement all the methods declared in the interface for implementing an interface.
- go language interfaces are implemented implicitly
- it does not contain any specific keyword to implement an interface
```go 
// to implement an interface
package main
import "fmt"

// Creating an interface
type tank interface {

	// Methods
	Tarea() float64
	Volume() float64
}

type myvalue struct {
	radius float64
	height float64
}

// Implementing methods of
// the tank interface
func (m myvalue) Tarea() float64 {

	return 2*m.radius*m.height +
		2*3.14*m.radius*m.radius
}

func (m myvalue) Volume() float64 {

	return 3.14 * m.radius * m.radius * m.height
}

// Main Method
func main() {

	// Accessing elements of
	// the tank interface
	var t tank
	t = myvalue{10, 14}
	fmt.Println("Area of tank :", t.Tarea())
	fmt.Println("Volume of tank:", t.Volume())
}
/*
Ouptut
Area of tank : 908
Volume of tank: 4396
*/
````
----
