# Go Loops

### Loops

- execute block of code repeatedly for a specified number of times till it meets  specified condition
- very useful to perform same task multiple times
- two types of loops :
    - For loop
    - Nested loop
- Loop controls :
    - alter or control the flow of loop execution based on specific conditions.
    - break
    - continue
    - goto

---

### For Loop

- two functions
    - counter-controlled iteration
    - Condition-controlled iteration
- When the execution of the loop is over, the objects created inside the loop gets destroyed.
- Syntax  `for initalization;conditional;increment{//body}`

```go
//Counter controlled for loop
package main

import "fmt"

func main() {
	for a := 0; a < 11; a++ {
		fmt.Print(a, "\n")
	}
}
//Output 
0
...
10
```

**Nested For Loop**: 

```go
package main  
import "fmt"  
func main() {  
   for a := 0; a < 3; a++ {  
      for b := 3;b > 0; b-- {  
         fmt.Print(a," ",b,"\n")  
      }  
   }  
}
//Output
0 3
0 2
0 1
1 3
1 2
1 1
2 3
2 2
2 1
```

**Go Infinitive For Loop :**

 `for i:=0; ; i++`  or  `for {}`

```go
package main  
import "fmt"  
func main() {  
   for true  {  
      fmt.Printf("This loop will run forever.\n");  
   }  
}
```

### Go for loop as a while loop

```go
package main

import "fmt"

func main() {
	power := 1
	for power < 5 {
		power *= 2
	}
	fmt.Println(power)
}
```

---

### Condition Controlled For iteration

- Syntax

 `for condition {}`

```go
package main  
import "fmt"  
func main() {  
   sum := 1  
   for sum < 100 {  
      sum += sum  
      fmt.Println(sum)  
   }  
}
```

[https://play.golang.org/p/Qw2Ei2jPr-K](https://play.golang.org/p/Qw2Ei2jPr-K)

---

### Go for range construct

- used to traverse every item in a collection
- similar to for-each  in other languages
- Syntax : `for ix,val := range coll{}`

```go
package main

import "fmt"

func main() {
	nums := []int{2, 3, 4}
	sum := 0
	for _, value := range nums {
		// "_" is to ignore the index
		sum += value
	}
	fmt.Println("sum: ", sum)
	for i, num := range nums {
		if num == 3 {
			fmt.Println("index: ", i)
		}
	}
	dict := map[string]string{
		"1": "mango",
		"2": "apple",
		"3": "banana",
	}
	for k, v := range dict {
		//k=> key,v=>value,
		//map is used for key value pair creation
		fmt.Printf("%s->%s\n", k, v)
	}
	for k := range dict {
		fmt.Println("keys: ", k)
	}
	for i, c := range "Hi" {
		fmt.Println(i, c)
	}
}
/* output 
sum: 9
1 -> mango
2 -> apple 
3 -> banana 
key: 1
key: 2
key: 3
0 72
1 105
*/
```

[https://play.golang.org/p/j56hd1BuEAN](https://play.golang.org/p/j56hd1BuEAN)

[https://play.golang.org/p/b0RfJPI6Fht](https://play.golang.org/p/b0RfJPI6Fht)

[https://play.golang.org/p/RWG1ZlBVeqZ](https://play.golang.org/p/RWG1ZlBVeqZ)

---

### Go Goto statement

- alter the normal execution of  a program and transfer control to a labeled statement in the same program
- label is an identifier
- Syntax  `goto label ... .. label:`

```go
package main

import "fmt"

func main() {
	var age int
election:
	fmt.Print("Enter your age")
	fmt.Scanln(&age)
	if age <= 17 {
		fmt.Print("You are not eligible to vote. \n")
		goto election
	} else {
		fmt.Print("You are eligible to vote.")
	}
}
```

[https://play.golang.org/p/-Ro7vIfab3B](https://play.golang.org/p/-Ro7vIfab3B)

---

### Go Break Statement

- used to break out of the innermost structure in which it occurs
- used for for-loop,switch
- Syntax `break;`

```go
package main

import "fmt"

func main() {
	var a int = 1
	for a < 10 {
		fmt.Print("Value of a is", a, "\n")
		a++
		if a > 5 {
			//terminate loop using break
			break
		}
	}
}
/*
Ouput
**Value of a is 1
Value of a is 2
Value of a is 3
Value of a is 4
Value of a is 5
*/**
```

**Break Statement with Inner Loop** 

```go
package main

import "fmt"

func main() {
	var a int
	var b int
	for a := 1; a <= 3; a++ {
		for b := 1; b <= 3; b++ {
			if a == 2 && b == 2 {
				break
			}
			fmt.Print(a, " ", b, "\n")
		}
	}
}
/* 
Output
**1 1
1 2
1 3
2 1
3 1
3 2
3 3
*/**
```

**Go Labeled break**

- terminate the part where the label is placed

```go
package main 
import "fmt"
func main(){
var count = 0
outer: 
for count <= 10{
count++
if(count == 5){
break outer 
}
fmt.Printf("Inside loop %d\n",count)
}
fmt.Println("Out of loop")
}
/* 
Output
Inside loop 1 
Inside loop 2
Inside loop 3
Inside loop 4 
Out of loop
*/
```

---

### Go Continue Statement

- a way to skip over the current iteration of any loop
- when continue statement is encountered Go ignores rest of statements in the loop body for current iteration and returns the program execution to the very first statement in the body.
- does not terminate the loop rather continue with the next iteration.

```go
//Syntax 
for <condition1>{
//body 
if (condition2){
continue 
}
// loop body
}
(or)
 x:  
 continue:x
```

```go
 //Example 
package main  
import "fmt"  
func main() {  
   /* local variable definition */  
   var a int = 1  
   /* do loop execution */  
   for a < 10 {  
      if a == 5 {  
         /* skip the iteration */  
         a = a + 1;  
         continue;  
      }  
      fmt.Printf("value of a: %d\n", a);  
      a++;  
   }  
}
/* 
Output 
value of a: 1
value of a: 2
value of a: 3
value of a: 4
value of a: 6
value of a: 7
value of a: 8
value of a: 9
*/
```

**Go continue statement with Inner Loop example**

```go
//Example 
package main  
import "fmt"  
func main() {  
   /* local variable definition */  
   var a int = 1  
   var b int = 1  
   /* do loop execution */  
   for a = 1; a < 3; a++ {  
      for b = 1; b < 3; b++ {  
         if a == 2 && b == 2 {  
            /* skip the iteration */  
            continue;  
         }  
         fmt.Printf("value of a and b is %d %d\n", a, b);  
      }  
      fmt.Printf("value of a and b is %d %d\n", a, b);  
   }  
}
/*
Output
value of a and b is 1 1
value of a and b is 1 2
value of a and b is 1 3
value of a and b is 2 1
value of a and b is 2 3
*/
```

**Labeled continue**

```go
package main

import "fmt"

func main() {
	var i = 0
	var j = 0
outerfor:
	for i < 3 {
		j = 0
		i++
		for j < 3 {
			j++
			fmt.Printf("i is %d and j is %d\n", i, j)
			if i == 2 {
				fmt.Println("Skip now")
				continue outerfor
			}
			fmt.Println("Print now")
		}
	}
}
/* 
Output
i is 1 and j is 1
Print now
i is 1 and j is 2
Print now
i is 1 and j is 3
Print now
i is 2 and j is 1
Skip now
i is 3 and j is 1
Print now
i is 3 and j is 2
Print now
i is 3 and j is 3
Print now
*/
```

---
<h4 align="left">
<p> 
   <a href="https://github.com/ZephyrAveryl777/Golang-Notes/blob/main/Decision%20Making/Go%20Decision%20Making.md"> Previous: Go Decision Making</a>
   </p>
</h4>


<h4 align="right">
<p>
<a href="https://github.com/ZephyrAveryl777/Golang-Notes/blob/main/Comments/Go%20Comments.md">Next: Go Comments </a>
<p>
</h4>
