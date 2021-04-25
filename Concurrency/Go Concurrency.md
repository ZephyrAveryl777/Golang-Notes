## Goroutines -- Concurrency in Golang

- A Goroutine is a function or method which executes independently and simultaneously in connection with any other Goroutines present in a program. 
- in simple words, every concurrently executing activity in Go language is known as a Goroutines.
- can consider a Goroutine as a light weighted thread. 
- The cost of creating Goroutines is very small as compared to the thread. 
- Every program contains at least a single Goroutine and that Goroutine is known as the **main Goroutine**. 
- All the Goroutines are working under the main Goroutines if the main Goroutine terminated, then all the goroutine present in the program also terminated. 
- Goroutine always works in the background.

#### Creating a Goroutine?
- can create your own Goroutine simply by using go keyword as a prefixing to the function or method call.
- **Syntax:**
    ```go
      func name(){
      // statements
      }

      // using go keyword as the
      // prefix of your function call
      go name()
    ```
    
- **Example:**

```go 
  // the concept of Goroutine
  package main

  import "fmt"

  func display(str string) {
      for w := 0; w < 6; w++ {
          fmt.Println(str)
      }
  }

  func main() {

      // Calling Goroutine
      go display("Welcome")

      // Calling normal function
      display("Go is amazing")
  }
  /*
  Output:
  Go is amazing
  Go is amazing
  Go is amazing
  Go is amazing
  Go is amazing
  Go is amazing
  */
````
- In the above example, the program  create a *display()* function and then call this function in two different ways first 
	- one is a Goroutine, i.e. *go display("Welcome")* and 
	- another one is a normal function, i.e. *display("Go is amazing")*. 
- there is a problem, it only displays the result of the normal function that does not display the result of Goroutine because when a new Goroutine executed, the Goroutine call return immediately. 
- The control does not wait for Goroutine to complete their execution just like normal function, always moves forward to the next line after the Goroutine call and ignores the value returned by the Goroutine. 
- to executes a Goroutine properly, some modifications are needed.

- **Modified Example:**
 ```go
  // Go program to illustrate the concept of Goroutine
  package main

  import (
      "fmt"
      "time"
  )

  func display(str string) {
      for w := 0; w < 6; w++ {
          time.Sleep(1 * time.Second)//go routine sleeps for 1 second
          fmt.Println(str)
      }
  }

  func main() {

      // Calling Goroutine
      go display("Welcome")

      // Calling normal function
      display("Go is amazing")
  }
  /*
  Output:

  Welcome
  Go is amazing
  Go is amazing
  Welcome
  Welcome
  Go is amazing
  Go is amazing
  Welcome
  Welcome
  Go is amazing
  Go is amazing
  */
```

#### Advantages of Goroutines

-   Goroutines are cheaper than threads.
-   Goroutine are stored in the stack and the size of the stack can grow and shrink according to the requirement of the program. But in threads, the size of the stack is fixed.
-   Goroutines can communicate using the channel and these channels are specially designed to prevent race conditions when accessing shared memory using Goroutines.
-    If any of Goroutine blocks the thread due to resource requirement then all the remaining Goroutines will assign to a newly created OS thread. All these details are hidden from the programmers.

#### Anonymous Goroutine

- can also start Goroutine for an anonymous function 
- by using go keyword as a prefix of that function 
- **Syntax:**
	```go
    // Anonymous function call
    go func (parameter_list){
    // statement
    }(arguments)
	```    
- **Example:**
```go
// to create an anonymous Goroutine
package main
  
import (
    "fmt"
    "time"
)
  
// Main function
func main() {
  
    fmt.Println("Welcome!! to Main function")
  
    // Creating Anonymous Goroutine
    go func() {
  
        fmt.Println("Welcome!! to Go Programming")
    }()
  
    time.Sleep(1 * time.Second)
    fmt.Println("GoodBye!! to Main function")
}
/*
Output:

Welcome!! to Main function
Welcome!! to Go Programming
GoodBye!! to Main function
*/
