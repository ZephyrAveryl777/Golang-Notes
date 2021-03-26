# Go Strings

### Strings

- Go string is a sequence of variable-width characters.
- Go strings and text files occupy less memory or disk space
- UTF-8 is the standard to encode and decode strings
- Strings are value types and immutable.
- initial value of a string is empty `""` by default

```go
package main  
import ("fmt"  
      "reflect"  
)  
func main()  {  
   var x string = "Hello World"  
   fmt.Println(x)  
   fmt.Println(reflect.TypeOf(x))  
}
/* 
Output 
Hello World
string 
*/
```

---

### Go String len()

```go
package main  
import "fmt"  
func main() {  
   str := "I love my country"  
   fmt.Println(len(str))  
}
/*
Output 
17 
*/  
```

---

### Go Print ASCII

```go
package main  
import "fmt"  
func main() {  
   fmt.Println("Ascii value of A is ","A"[0])  
}
/*
Output 
Ascii value of A is  65
*/
```

---

### Go String ToUpper()

```go
package main  
import "fmt"  
import "strings"  
func main() {  
   str := "india"  
   fmt.Println(strings.ToUpper(str))  
}
/* 
Output 
INDIA
*/
```

---

### Go String HasPrefix()

```go
package main  
import "fmt"  
import "strings"  
func main() {  
   s := "INDIA"  
   fmt.Println(strings.HasPrefix(s,"IN"))  
}
/* Output 
ture 
*/
```

---

### Go String HasSuffix()

```go
package main  
import "fmt"  
import "strings"  
func main() {  
   s := "INDIA"  
   fmt.Println(strings.HasSuffix(s,"IA"))  
}
/*
Output
true
*/
```

---

### Go String Join()

```go
package main  
import "fmt"  
import "strings"  
func main() {  
   var arr = []string{"a","b","c","d"}  
   fmt.Println(strings.Join(arr,"*"))  
} 
/*
Output: a*b*c*d
*/
```

---

### Go String Repeat()

```go
package main
import "fmt"
import "string"
func main(){
 var str = "New" 
fmt.Println(strings.Repeat(str,4))
}
/*
Output: New New New New
*/
```

---

### Go String Contains()

```go
package main
import "fmt"
import "strings"
func main(){
	str := "Hi...hello!!!"
	fmt.Println(strings.Contains(str,"th"))
}
/*
Output: true
*/ 
```

---

### Go String Index()

```go
package main
import "fmt"
import "strings"
func main(){
	str := "Hi...Hello there!!!"
	fmt.Println(strings.Index(str,"th"))
}
/*
Output: 5
*/
```

---

### Go String Count()

```go
package main
import "fmt"
import "strings"
func main(){
	 str := "Hi there" 
	 fmt.Println(strings.Count(str,"e"))
}
/*
Output: 3
*/
```

---

### Go String Replace()

```go
package main
import "fmt"
import "strings"
func main(){
	str := "Hi there"
	fmt.Println(strings.Replace(str,"e","Z",2))
}
/*
Output: Hi thZrZ 
*/
```

---

### Go String Split()

```go
// Example 1 
package main
import "fmt"
import "strings"
func main(){
	str:= "I love my coding" 
	var arr []string = strings.Split(str," ")
	fmt.Println(len(arr))
	for i,v := range arr{
		fmt.Println("Index : ",i,"value : ",v)
}
}
/*
Output : 
4
Index :  0 value :  I
Index :  1 value :  love
Index :  2 value :  my
Index :  3 value :  coding
*/

// Example 2
package main 
import (
	"fmt"
	"strings"
)
func main(){
	fmt.Printf("%q\n",strings.Split("x,y,z",","))
	fmt.Printf("%q\n",strings.Split("Jack and Jill went up the hill","&"))
	fmt.Printf("%q\n",strings.Split("abc",""))
	fmt.Printf("%q\n",strings.Split("","Hello"))
}
/*
Output: 
["x" "y" "z"]
[" John " " Jack " " Johnny " " Jinn"]
[" " "a" "b" "c" " "]
[""]
*/ 
```

---

### Go String Compare()

```go
package main
import (
	"fmt"
	"strings"
)
func main(){
	fmt.Println(strings.Compare("a","b"))
	fmt.Println(strings.Compare("a","a"))
	fmt.Println(strings.Compare("b","a"))
}
/*
Output: 
 -1
 0
 1
}
*/
```

---

### Go String Trim()

```go
package main
import (
	"fmt"
	"strings"
)
func main(){
	fmt.Println("strings.Trimspace("\t\n I love my coding"))
}
/*
Output:
  I love my coding
```

---

### Go String ContainsAny()

```go
package main
import (
		"fmt"
		"strings"
)
func main(){
	fmt.Println(strings.ContainsAny("Hello","A"))
	fmt.Println(strings.ContainsAny("Hello","o & e"))
	fmt.Println(strings.ContainsAny("Hello",""))
	fmt.Println(strings.ContainsAny("",""))
}
/*
Output: 
false
true
false
false 
*/
```

---
