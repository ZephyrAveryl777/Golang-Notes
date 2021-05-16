# Go Regex

## Regex

- used for searching string.
- pattern of search is provided
- methods can be invoked through regex to compile the pattern of search
- regex objects can be retrieved by using compile() and must compile() functions., to find strings such as FindString(), FindStringSubmatch(), FindStringIndex()

```go
//Example 1
package main
import (
	"fmt"
	"regex"
)
func main(){
	re := regexp.MustCompile(".com")
	fmt.Println(re.FindString("google.com"))
	fmt.Println(re.FindString("abc.org"))
	fmr.Println(re.FindString("fb.com"))
}
/*
Output: 
.com
.com
*/
```

- FindString() returns a string having the text of the last most match. if no match is found, empty string is returned.

```go
package main
import (
	"fmt"
	"regexp"
)
func main() {
	re := regexp.MustCompile(".com")
	fmt.Println(re.FindStringIndex("google.com"))
	fmt.Println(re.FindStringIndex("abc.com"))
	fmt.Println(re.FindStringIndex("fb.com"))
}
/* 
Output: 
	[6 10]
	[]
	[2 6]
*/
```

---

- FindStringSubmatch() method returns a slice of string having the text of the leftmost match and the matches . If no match found, returns value as an empty string.

```go
//Example 3
package main
import (
	"fmt"
	"regexp"
)
func main(){
	re := regexp.MustCompile("f(a-z]+)ing")
	fmt.Println(re.FindStringSubmatch("flying"))
	fmt.Println(re.FindStringSubmatch("abcfloatingxyz"))
}
/*
Output: 
[flying ly]
[floating loat]

Process finished with exit code 0
*/ 
```

---
<h4 align="left">
<p> 
   <a href="https://github.com/ZephyrAveryl777/Golang-Notes/blob/main/Strings/Go%20Strings.md"> Previous: Go Strings</a>
   </p>
</h4>
