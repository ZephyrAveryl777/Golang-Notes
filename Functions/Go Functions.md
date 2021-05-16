# Go Functions

### Functions

- basic building blocks
- break large problems into smaller tasks
- code re-usability
- three types of functions :
    - Normal functions with an identifier
    - Anonymous or lambda functions
    - Method (A function with a receiver)
- Function parameters, return values, together with types, is called function signature.
- cannot be declared inside another function, need anonymous function.
- Syntax  `func (receiver) identifier(parameters) (returns) { code }`
    - we define our function with parameters (if any)
    - we call our function and pass in arguments (in any)
- Everything in Go is PASS BY VALUE

```go
package main 
import "fmt"
type Employee struct{
	fname string 
	lname string 
}
func (emp Employee)fullname(){
	fmt.Println(emp.fname+" "+emp.lname)
}
func main(){
	e1 := Employee{"Ricky","Ponting"} 
	e1.fullname()
}
/*
Output
Ricky Ponting 
*/ 
```

**Go Function with Return**

```go
package main 
import "fmt"
func fun() int {
	return 123456789
}
func main(){
	x := fun()
	fmt.Println(x)
}
/*
Output
123
*/ 
```

**Go function with multiple return**

```go
package main  
import (  
   "fmt"  
)  
func main() {  
   fmt.Println(addAll(10,15,20,25,30))  
}  
func addAll(args ... int)(int,int)  {  
   finalAddValue:=0  
   finalSubValue:=0  
   for _,value  := range args{  
      finalAddValue += value  
      finalSubValue -= value  
   }  
	//parallel assignment 
   return finalAddValue,finalSubValue  
}
/*
Output 
100 -100
*/
```

---

### Variadic Parameter

- a function which takes an unlimited number of arguments.
- When use the lexical element operator “...T” to signify a
variadic parameter (there “T” represents some type)

[https://play.golang.org/p/l6pbuFDz_eP](https://play.golang.org/p/l6pbuFDz_eP)

---

### Unfurling a slice

When you have a slice of some type, you can pass in the individual values in a slice by using the “...” operator.

- unfurling a slice of int.

    [https://play.golang.org/p/doo199ZzYtT](https://play.golang.org/p/doo199ZzYtT)

- passing in zero or more values .

    [https://play.golang.org/p/LXLjBIDkQSC](https://play.golang.org/p/LXLjBIDkQSC)

- variadic parameter has to be the final parameter

    [https://play.golang.org/p/vCvkqpe1CIs](https://play.golang.org/p/vCvkqpe1CIs)

---

### Defer

- A "defer" statement invokes a function whose execution is deferred to the moment the surrounding function returns, either because the surrounding function executed a return statement, reached the end of its function body, or because the corresponding goroutine is panicking

[https://play.golang.org/p/dUYiD9R4vqq](https://play.golang.org/p/dUYiD9R4vqq)

---

### Methods :

- A method is nothing more than a function attached to a type
- attach a function to a type with a RECEIVER

[https://play.golang.org/p/AKrvuxF0wMK](https://play.golang.org/p/AKrvuxF0wMK)

---

### Interfaces & Polymorphism

- values in Go can of more than one type by the use of interface
- Syntax  `type <name> interface`
- can define which methods a type must have to implement that interface.

[https://play.golang.org/p/RKezV69HjPe](https://play.golang.org/p/RKezV69HjPe)

---

### Anonymous function

- Anonymous self-executing function

[https://play.golang.org/p/wTKHFo8ryvQ](https://play.golang.org/p/wTKHFo8ryvQ)

---

### Function Expression

- Assigning a function to a variable

[https://play.golang.org/p/cj6k_CQWP-6](https://play.golang.org/p/cj6k_CQWP-6)

---

### Returning a function

- can return a function from a function
    - returning a string

        [https://play.golang.org/p/GzNV2-meQTb](https://play.golang.org/p/GzNV2-meQTb)

    - returning a function

        [https://play.golang.org/p/FaEKvXkKQ9H](https://play.golang.org/p/FaEKvXkKQ9H)

    ---

### Callback

- passing a function as an argument
- functional programming not recommended in go, it is good to be aware of callbacks
- idiomatic go: write clear, simple readable code

[https://play.golang.org/p/2CJ1TYzv37b](https://play.golang.org/p/2CJ1TYzv37b)

---

### Closure

- one scope enclosing other scopes
    - variables declared in the outer scope are accessible in inner scopes
- closure helps us limit the scope of variables

```go
package main  
import (  
   "fmt"  
)  
func main() {  
   number := 10  
      squareNum := func() (int){  
      number *= number  
      return number  
   }  
   fmt.Println(squareNum())  
   fmt.Println(squareNum())  
}
```

[https://play.golang.org/p/YWuniJtu2R](https://play.golang.org/p/YWuniJtu2R)

[https://play.golang.org/p/4hqrzybcFc](https://play.golang.org/p/4hqrzybcFc)

[https://play.golang.org/p/6Hyqe_aU-R](https://play.golang.org/p/6Hyqe_aU-R)

[https://play.golang.org/p/fHez3lg8wc](https://play.golang.org/p/fHez3lg8wc)

---

### Recursion

- calling same function from within the function
- break situation into multiple tasks

```go
package main  
import (  
   "fmt"  
)  
func main() {  
   fmt.Println(factorial(5))  
}  
func factorial(num int ) int{  
   if num == 0{  
      return 1  
   }  
   return num*factorial(num-1)  
}
```

---
<h4 align="left">
<p> 
   <a href="https://github.com/ZephyrAveryl777/Golang-Notes/blob/main/Type%20Casting/Go%20TypeCasting.md"> Previous: Go TypeCasting</a>
   </p>
</h4>


<h4 align="right">
<p>
<a href="https://github.com/ZephyrAveryl777/Golang-Notes/blob/main/Arrays/Go%20Arrays.md">Next: Go Arrays </a>
<p>
</h4>
