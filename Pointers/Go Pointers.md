## Pointers in Go 
- Pointers is a variable which is used to store the memory address of another variable. 
- In Golang its also termed as the special variables. 
- variables are used to store some data at a particular memory address in the system. 
- memory address is always found in hexadecimal format(starting with 0x like 0xFFAAF etc.).

**Need for Pointers**
- Variables are the names given to a memory location where the actual data is stored. 
- To access the stored data the address of that particular memory location is needed. 
- To remember all the memory addresses(Hexadecimal Format) manually is an overhead that's why use of variables to store data 
- as variables can be accessed just by using their name.
- Golang also allows saving a hexadecimal number into a variable using the literal expression i.e. number starting from **0x** is a hexadecimal number.
- **Example**
```Go
// variables storing the hexadecimal values
package main

import "fmt"

func main() {

	// storing the hexadecimal
	// values in variables
	x := 0xFF
	y := 0x9C
	
	// Displaying the values
	fmt.Printf("Type of variable x is %T\n", x)
	fmt.Printf("Value of x in hexdecimal is %X\n", x)
	fmt.Printf("Value of x in decimal is %v\n", x)
	
	fmt.Printf("Type of variable y is %T\n", y)
	fmt.Printf("Value of y in hexdecimal is %X\n", y)
	fmt.Printf("Value of y in decimal is %v\n", y)	
	
}

/*
Output:

Type of variable x is int
Value of x in hexdecimal is FF
Value of x in decimal is 255
Type of variable y is int
Value of y in hexdecimal is 9C
Value of y in decimal is 156
*/
```
- Pointer is generally termed as Special kind of Variable because it is almost declared as a variable but with \* **(dereferencing operator)**.

[![Pointers-in-Golang](https://media.geeksforgeeks.org/wp-content/uploads/20190705160332/Pointers-in-Golang.jpg)](https://media.geeksforgeeks.org/wp-content/uploads/20190705160332/Pointers-in-Golang.jpg)

---

#### Declaration and Initialization of Pointers

- there are two important operators used in pointers:
    - \* **Operator** also termed as the _dereferencing operator_ used to declare pointer variable and access the value stored in the address.
    - **& Operator** termed as _address operator_ used to returns the address of a variable or to access the address of a variable to a pointer.

- **Declaring a pointer**:
    - Syntax `var pointer_name *Data_Type`
    - Example 
    ```go
    var s *string
    ```
- **Initialization of Pointer:** 
    - to initialize a pointer with the memory address of another variable can be done with the help of address operator 
    ```go
      // normal variable declaration
      var a = 45

      // Initialization of pointer s with
      // memory address of variable a
      var s *int = &a
    ```
    
    - **Example:**
    ```go
    // Golang program to demonstrate the declaration
    // and initialization of pointers
    package main

    import "fmt"

    func main() {

      // taking a normal variable
      var x int = 5748

      // declaration of pointer
      var p *int

      // initialization of pointer
      p = &x

        // displaying the result
      fmt.Println("Value stored in x = ", x)
      fmt.Println("Address of x = ", &x)
      fmt.Println("Value stored in variable p = ", p)
    }
    /*
    Output:
    Value stored in x =  5748
    Address of x =  0x414020
    Value stored in variable p =  0x414020
    */
    ```

---

### Important Points:

-   The default value or zero-value of a pointer is always **nil**(NILL). Or an uninitialized pointer will always have a nil value.

    - *Example:*
    ```Go
    // demonstrate the nil value of the pointer
    package main

    import "fmt"

    func main() {

        // taking a pointer
      var s *int

      // displaying the result
      fmt.Println("s = ", s)
    }
    /*
    Output:
    s =  <nil>
    */
    ```

-   Declaration and initialization of the pointers can be done into a single line.

    - *Example:*
    ```go
    var s *int = &a
    ```
-  If you are specifying the data type along with the pointer declaration then the pointer will be able to handle the memory address of that specified data type variable. 
-  _Example_: if taking a pointer of string type then the address of the variable given to a pointer will be only of string data type variable, not any other type.
-   To overcome the above mention problem, can use the Type Inference, there is no need to specify the data type of during the declaration. 
-   The type of a pointer variable can also be determined by the compiler like a normal variable. 
    -   *Example:*
    ```go 
    // the use of type inference in
    // Pointer variables
    package main

    import "fmt"

    func main() {

      // using var keyword
      // we are not defining
      // any type with variable
      var y = 458

      // taking a pointer variable using
      // var keyword without specifying
      // the type
      var p = &y

      fmt.Println("Value stored in y = ", y)
      fmt.Println("Address of y = ", &y)
      fmt.Println("Value stored in pointer variable p = ", p)
    }
    /*
    Output:
    Value stored in y =  458
    Address of y =  0x414020
    Value stored in pointer variable p =  0x414020
    */
    ```
-  can also use the *shorthand (:=)* syntax to declare and initialize the pointer variables. 
-  The compiler will internally determine the variable is a pointer variable if we are passing the address of variable using *&(address)* operator to it.
   - *Example:*
    ```go
    // the use of shorthand syntax in
    // Pointer variables
    package main

    import "fmt"

    func main() {

      // using := operator to declare
      // and initialize the variable
      y := 458

      // taking a pointer variable using
      // := by assigning it with the
      // address of variable y
      p := &y

      fmt.Println("Value stored in y = ", y)
      fmt.Println("Address of y = ", &y)
      fmt.Println("Value stored in pointer variable p = ", p)
    }
    /*
    Output:
    Value stored in y =  458
    Address of y =  0x414020
    Value stored in pointer variable p =  0x414020
    */
    ```

#### Dereferencing the Pointer
- * operator is also termed as the dereferencing operator. 
- It is not only used to declare the pointer variable but also used to access the value stored in the variable which the pointer points to which is generally termed as **indirecting or dereferencing**. 
- \* operator is also termed as the value at the address of. 
  - **Example:**
 ```go
    // concept of dereferencing a pointer
    package main

    import "fmt"

    func main() {

      // using var keyword
      // we are not defining
      // any type with variable
      var y = 458

      // taking a pointer variable using
      // var keyword without specifying
      // the type
      var p = &y

      fmt.Println("Value stored in y = ", y)
      fmt.Println("Address of y = ", &y)
      fmt.Println("Value stored in pointer variable p = ", p)

      // this is dereferencing a pointer
      // using * operator before a pointer
      // variable to access the value stored
      // at the variable at which it is pointing
      fmt.Println("Value stored in y(*p) = ", *p)

    }
    /*
    Output:

    Value stored in y =  458
    Address of y =  0x414020
    Value stored in pointer variable p =  0x414020
    Value stored in y(*p) =  458
    */
```
-  can also change the value of the pointer or at the memory location instead of assigning a new value to the variable.
    - **Example:**
    ```go
    package main

    import "fmt"

    func main() {
      // using var keyword
      // we are not defining
      // any type with variable
      var y = 458

      // taking a pointer variable using
      // var keyword without specifying
      // the type
      var p = &y

      fmt.Println("Value stored in y before changing = ", y)
      fmt.Println("Address of y = ", &y)
      fmt.Println("Value stored in pointer variable p = ", p)

      // this is dereferencing a pointer
      // using * operator before a pointer
      // variable to access the value stored
      // at the variable at which it is pointing
      fmt.Println("Value stored in y(*p) Before Changing = ", *p)

      // changing the value of y by assigning
      // the new value to the pointer
      *p = 500

      fmt.Println("Value stored in y(*p) after Changing = ",y)

    }
    /*
    Output:
    Value stored in y before changing =  458
    Address of y =  0x414020
    Value stored in pointer variable p =  0x414020
    Value stored in y(*p) Before Changing =  458
    Value stored in y(*p) after Changing =  500
    */
    ```

---

## Pointer to Pointer (Double Pointer )
- A pointer can point to a variable of any type even to a pointer. 
- this looks like a chain of pointers. When 
- when define a pointer to pointer then the first pointer is used to store the address of the second pointer. 
- This concept is sometimes termed as **Double Pointers**.
#### Declaration of Double Pointer 
- Declaring Pointer to Pointer is similar to declaring pointer in go 
- The difference is we have to place an additional '*****' before the name of pointer name. 
- This is generally done while declaring the pointer variable using the var keyword along with the type. 
- **Example**:

[![Double Pointer in Go](https://media.geeksforgeeks.org/wp-content/uploads/20190710183146/Pointer-To-Pointer.jpg)](https://media.geeksforgeeks.org/wp-content/uploads/20190710183146/Pointer-To-Pointer.jpg)
```go
// concept of the Pointer to Pointer
package main
   
import "fmt"
   
// Main Function
func main() {
   
        // taking a variable
        // of integer type
    var V int = 100
       
    // taking a pointer 
    // of integer type 
    var pt1 *int = &V
       
    // taking pointer to 
    // pointer to pt1
    // storing the address 
    // of pt1 into pt2
    var pt2 **int = &pt1
   
    fmt.Println("The Value of Variable V is = ", V)
    fmt.Println("Address of variable V is = ", &V)
   
    fmt.Println("The Value of pt1 is = ", pt1)
    fmt.Println("Address of pt1 is = ", &pt1)
   
    fmt.Println("The value of pt2 is = ", pt2)
   
    // Dereferencing the 
    // pointer to pointer
    fmt.Println("Value at the address of pt2 is or *pt2 = ", *pt2)
       
    // double pointer will give the value of variable V
    fmt.Println("*(Value at the address of pt2 is) or **pt2 = ", **pt2)
}
/*
Output:

The Value of Variable V is =  100
Address of variable V is =  0x414020
The Value of pt1 is =  0x414020
Address of pt1 is =  0x40c128
The value of pt2 is =  0x40c128
Value at the address of pt2 is or *pt2 =  0x414020
*(Value at the address of pt2 is) or **pt2 =  100
*/
```

- **Example 2:**

[![How Pointers Works In Go](https://media.geeksforgeeks.org/wp-content/uploads/20190710182934/HowPointersWorksInGo.png)](https://media.geeksforgeeks.org/wp-content/uploads/20190710182934/HowPointersWorksInGo.png)
```go
package main
   
import "fmt"
   
// Main Function
func main() {
   
        // taking a variable
        // of integer type
    var V int = 100
       
    // taking a pointer 
    // of integer type 
    var pt1 *int = &V
       
    // taking pointer to 
    // pointer to pt1
    // storing the address 
    // of pt1 into pt2
    var pt2 **int = &pt1
   
    fmt.Println("The Value of Variable V is = ", V)
    fmt.Println("Address of variable V is = ", &V)
   
    fmt.Println("The Value of pt1 is = ", pt1)
    fmt.Println("Address of pt1 is = ", &pt1)
   
    fmt.Println("The value of pt2 is = ", pt2)
   
    // Dereferencing the 
    // pointer to pointer
    fmt.Println("Value at the address of pt2 is or *pt2 = ", *pt2)
       
    // double pointer will give the value of variable V
    fmt.Println("*(Value at the address of pt2 is) or **pt2 = ", **pt2)
}

/*
Output

The Value of Variable v is =  100
Value stored in v after changing pt1 =  200
Value stored in v after changing pt2 =  300
*/
```
---

## Pointers to a Function in Go

-  You can also pass the pointers to the function like the variables. 
-  There are two ways to do this as follows:
    -   **Create a pointer and simply pass it to the function**
    -   **Passing an address of the variable**

#### Create a pointer and simply pass it to the Function

```GO
package main
  
import "fmt"
  
// taking a function with integer
// type pointer as an parameter
func ptf(a *int) {
  
    // dereferencing
    *a = 748
}
  
// Main function
func main() {
  
    // taking a normal variable
    var x = 100
  
        fmt.Printf("The value of x before function call is: %d\n", x)
  
    // taking a pointer variable
    // and assigning the address
    // of x to it
    var pa *int = &x
  
    // calling the function by
    // passing pointer to function
    ptf(pa)
  
    fmt.Printf("The value of x after function call is: %d\n", x)
  
}
/*
Output:

The value of x before function call is: 100
The value of x after function call is: 748
*/
```

#### Passing an address of the variable to the function call

```go
package main
  
import "fmt"
  
// taking a function with integer
// type pointer as an parameter
func ptf(a *int) {
  
    // dereferencing
    *a = 748
}
  
// Main function
func main() {
  
    // taking a normal variable
    var x = 100
      
    fmt.Printf("The value of x before function call is: %d\n", x)
  
    // calling the function by
    // passing the address of
    // the variable x
    ptf(&x)
  
    fmt.Printf("The value of x after function call is: %d\n", x)
  
}
/*
Output:

The value of x before function call is: 100
The value of x after function call is: 748
*/
```

>**Note:** 
> - can also use the short declaration operator(:=) to declare the variables and pointers in above programs.

---
## Pointer to an Array as a Function Argument 

- can use the pointers to an array and pass that one as an argument to the function.
- **Example**
```go
// pass a pointer to an array as an argument to the function
package main
  
import "fmt"
  
// taking a function
func updatearray(funarr *[5]int) {
  
    // updating the array value
    // at specified index
    (*funarr)[4] = 750
      
    // you can also write 
    // the above line of code
    // funarr[4] = 750
}
  
// Main Function
func main() {
  
    // Taking an pointer to an array
    arr := [5]int{78, 89, 45, 56, 14}
  
    // passing pointer to an array
    // to function updatearray
    updatearray(&arr)
  
    // array after updating
    fmt.Println(arr)
}
/*
Output:

[78 89 45 56 750]
*/
```
> **Note:**
> - In Golang it is not recommended to use Pointer to an Array as an Argument to Function as the code become difficult to read. 
> - it is not considered a good way to achieve this concept. To achieve this you can use slice instead of passing pointers.

- **Example:**
```go
// concept of passing a pointer to an
// array as an argument to the function
// using a slice
package main
  
import "fmt"
  
// taking a function
func updateslice(funarr []int) {
  
    // updating the value
    // at specified index
    funarr[4] = 750
}
  
// Main Function
func main() {
  
    // Taking an slice
    s := [5]int{78, 89, 45, 56, 14}
  
    // passing slice to the
    // function updateslice
    updateslice(s[:])
  
    // displaying the result
    fmt.Println(s)
}
/*
Output:

[78 89 45 56 750]
*/
```
---

## Pointer to a Struct in Golang

- You can also use a pointer to a **struct**.
- To use pointer to a struct, you can use **&** operator i.e. address operator. 
- Golang allows access to the fields of a structure using the pointers without any dereferencing explicitly.
- **Example 1:**
```go
// concept of the Pointer to struct
package main
  
import "fmt"
  
// taking a structure
type Employee struct {
  
    // taking variables
    name  string
    empid int
}
  
// Main Function
func main() {
  
    // creating the instance of the
    // Employee struct type
    emp := Employee{"ABC", 19078}
  
    // Here, it is the pointer to the struct
    pts := &emp
  
    fmt.Println(pts)
  
    // accessing the struct fields(liem employee's name)
    // using a pointer but here we are not using
    // dereferencing explicitly
    fmt.Println(pts.name)
  
    // same as above by explicitly using
    // dereferencing concept
    // means the result will be the same
    fmt.Println((*pts).name)
  
}
/*
Output:

&{ABC 19078}
ABC
ABC
*/
```

**Example 2:** 
- can also modify the values of the structure members or structure literals by using the pointer as shown below:
```go 
// concept of the Pointer to struct
package main
  
import "fmt"
  
// taking a structure
type Employee struct {
  
    // taking variables
    name  string
    empid int
}
  
// Main Function
func main() {
  
    // creating the instance of the
    // Employee struct type
    emp := Employee{"ABC", 19078}
  
    // Here, it is the pointer to the struct
    pts := &emp
  
    // displaying the values
    fmt.Println(pts)
  
    // updating the value of name
    pts.name = "XYZ"
  
    fmt.Println(pts)
  
}
/*
Output:

&{ABC 19078}
&{XYZ 19078}
*/
```
---
## Pointer Comparison 
- Go allowes to compare two pointers with each other. 
- Two pointers values are only equal when they point to the same value in the memory or if they are nil. 
- can perform a comparison on pointers with the help of == and != operators.

1. **== operator**: 
	-  This operator return true if both the pointer points to the same variable. Or return false if both the pointer points to different variables.
	- Syntax:
		`pointer_1 == pointer_2`
	- Example:
```go
      // concept of comparing two pointers
      package main

      import "fmt"

      func main() {

          val1 := 2345
          val2 := 567

          // Creating and initializing pointers
          var p1 *int
          p1 = &val1
          p2 := &val2
          p3 := &val1

          // Comparing pointers 
          // with each other
          // Using == operator
          res1 := &p1 == &p2
          fmt.Println("Is p1 pointer is equal to p2 pointer: ", res1)

          res2 := p1 == p2
          fmt.Println("Is p1 pointer is equal to p2 pointer: ", res2)

          res3 := p1 == p3
          fmt.Println("Is p1 pointer is equal to p3 pointer: ", res3)

          res4 := p2 == p3
          fmt.Println("Is p2 pointer is equal to p3 pointer: ", res4)

          res5 := &p3 == &p1
          fmt.Println("Is p3 pointer is equal to p1 pointer: ", res5)
      }
      /*
      Output:
      
      Is p1 pointer is equal to p2 pointer:  false
      Is p1 pointer is equal to p2 pointer:  false
      Is p1 pointer is equal to p3 pointer:  true
      Is p2 pointer is equal to p3 pointer:  false
      Is p3 pointer is equal to p1 pointer:  false
      */
```

2. **!= operator**: 
	- This operator return false if both the pointer points to the same variable. Or return true if both the pointer points to different variables.
	- Syntax:
		`pointer_1 != pointer_2`
	- Example:
		
```GO
        // concept of comparing two pointers
        package main

        import "fmt"

        func main() {

            val1 := 2345
            val2 := 567

            // Creating and initializing pointers
            var p1 *int
            p1 = &val1
            p2 := &val2
            p3 := &val1

            // Comparing pointers
            // with each other
            // Using != operator
            res1 := &p1 != &p2
            fmt.Println("Is p1 pointer not equal to p2 pointer: ", res1)

            res2 := p1 != p2
            fmt.Println("Is p1 pointer not equal to p2 pointer: ", res2)

            res3 := p1 != p3
            fmt.Println("Is p1 pointer not equal to p3 pointer: ", res3)

            res4 := p2 != p3
            fmt.Println("Is p2 pointer not equal to p3 pointer: ", res4)

            res5 := &p3 != &p1
            fmt.Println("Is p3 pointer not equal to p1 pointer: ", res5)
        }
        /*
        Output:

        Is p1 pointer not equal to p2 pointer:  true
        Is p1 pointer not equal to p2 pointer:  true
        Is p1 pointer not equal to p3 pointer:  false
        Is p2 pointer not equal to p3 pointer:  true
        Is p3 pointer not equal to p1 pointer:  true
		*/
```

---
## Pointer Capacity 
- In pointers, you are allowed to find the capacity of the pointer with the help of **cap()** function. 
- This function is a built-in function returns the capacity of the pointer to array.
- capacity defines the maximum number of elements stored in a pointer to array. 
- **Syntax:**
	`func cap(l Type) int`
- **Example:**
```go 
// capacity of the pointer to an array
package main
  
import (
    "fmt"
)
  
// Main function
func main() {
  
    // Creating and initializing
    // pointer to array
    // Using var keyword
    var ptr1 [7]*int
    var ptr2 [5]*string
    var ptr3 [8]*float64
  
    // Finding the capacity of
    // the pointer to array
    // Using cap function
    fmt.Println("Capacity of ptr1: ", cap(ptr1))
    fmt.Println("Capacity of ptr2: ", cap(ptr2))
    fmt.Println("Capacity of ptr3: ", cap(ptr3))
  
}
/*
Output:

Capacity of ptr1 : 7
Capacity of ptr2 : 5
Capacity of ptr3 : 8
*/
```
- **Example 2:**
```go
// capacity of the pointer to an array
package main
  
import (
    "fmt"
)
  
// Main function
func main() {
  
    // Creating an array
    arr := [8]int{200, 300, 400,
       500, 600, 700, 100, 200}
      
    var x int
  
    // Creating pointer
    var p [5]*int
  
    // Assigning the address
    for x = 0; x < len(p); x++ {
        p[x] = &arr[x]
    }
  
    // Displaying result
    for x = 0; x < len(p); x++ {
      
        fmt.Printf("Value of p[%d] = %d\n",
                                 x, *p[x])
    }
  
    // Finding capacity
    // using cap() function
    fmt.Println("Capacity of arr: ", cap(arr))
    fmt.Println("Capacity of p: ", cap(p))
}

**Output:**

Value of p[0] = 200
Value of p[1] = 300
Value of p[2] = 400
Value of p[3] = 500
Value of p[4] = 600
Capacity of arr:  8
Capacity of p:  5
```

---


