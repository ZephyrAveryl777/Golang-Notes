# Go Variables

### Variables

- represent reserved memory locations to store values
- Go is statically typed programming language → have to specify type associated with it and that cannot be changed
- Syntax  `var <name> <tag> / var <name> <tag> = <expression>`

```go
/*Variables in Golang*/
package main 
import "fmt"

func main(){
	 var hello string 
	 hello = "Hello World"
	 fmt.Println(hello)

//Output => Hello World
```

---

### The var Keyword

- parems ( )
- curly braces { }
- where var can be used
    - any place within the package
- scope
    - where a variable exists and is accessible
    - best practice: keep scope as “narrow” as possible

---

### Practice Code

[https://play.golang.org/p/iXJaHEZztc](https://play.golang.org/p/iXJaHEZztc)

[https://play.golang.org/p/Y-jFwR11N3u](https://play.golang.org/p/Y-jFwR11N3u)
