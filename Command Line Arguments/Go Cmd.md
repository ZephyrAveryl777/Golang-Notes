# Go Command Line Arguments

### Command Line Argument

- The arguments passed from the console can be received by the Go program and it can be used as an input.
- The os.Args is used to get the arguments.
- The index 0 of os.Args contains the path of the program.
- The os.Args[1:] holds provided arguments.

```go
package main  
  
import (  
    "fmt"  
    "os"  
)  
func main() {  
    var s, arg string  
    for i := 1; i < len(os.Args); i++ {  
        s += arg + os.Args[i]+" "  
    }  
    fmt.Print(s)  
}
/* 
Command to run the program 
go build ProgramName.go  
./ProgramName Tom and Jerry

Output
Tom and Jerry
*/
```

```go
package main  
import "os"  
import "fmt"  
func main() {  
    arumentWithPath := os.Args 
//returns all arguments including path  
    arumentSlice:= os.Args[1:] 
//returns all elements after path  
    arumentAt2 := os.Args[2] 
//returns specified argument only   
    fmt.Println(arumentWithPath)  
    fmt.Println(arumentSlice)  
    fmt.Println(arumentAt2)  
}
/*
Output 
[/private/var/folders/123/T/___cmd_go Tom and Jerry]
[Tom and Jerry]
and
Jerry

*/
```

---
