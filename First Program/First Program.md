# First Program

Learned: Feb 25, 2021 8:59 AM

### Go Hello World Example

Step 1 :-  Create  a file  <filename.go> use any text editor or IDE and specify .go file extension .

Step 2:-   

```go
/*First Go Program*/
package main 
import "fmt"
func main(){
	fmt.Println("Hello World!")
}
//Output => Hello World 
```

Step 3: - Open terminal or command prompt specify the folder where the above file is saved and run `go run <filename.go>` 

---

### Basic Program Structure

1. Documentation Block  & Package Declaration Block
    - any thing within `/* */`  is used to describe the program called documentation
    - `package main` (defining of Package happens here)
2. Pre-processor Statement 
    - `import "fmt"`  pre-processor statements(like import) tells the compiler what to do  prior to compilation of any Go program
3. The main() function 
    - func main
        - entry point to program
        - when code exits func main, program is terminated (over).
4. lcoal variables declaration
    - declare all the variables that will be used in func main() `var i int, i:=10`  (Example)
5. Program statements
    - Main logic of the program includes executable statements, loops and as on.
6. User defined functions 
    - custom functions are defined here
- to test the code

[https://play.golang.org/p/v3rrZLwEUC](https://play.golang.org/p/v3rrZLwEUC)

---
