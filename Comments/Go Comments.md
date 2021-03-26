# Comments in GO

### Comments

- set of statements not executed by the compiler / interpreter
- used for ease of understanding
- ignored during the execution of the program
- `//` (double forward slash) used for a single line comment

```go
package main
import "fmt"
func main(){
	// It prints Hello World 
	fmt.Println("Hello World")
}
```

- `/*..*/`   used for multiple line comment
- everything inside `/*...*/` is ignored by the compiler

```go
package mian
import "fmt"
func main(){
/* It prints 
Hello World! */
	fmt.Println("Hello World!")
}
```

---
