# Go Arrays

### Arrays

- homogeneous data structure (Fix type) and has a fixed-length
- a numbered sequence of elements of a single type
- used for Go internals, generally not recommended
- Syntax : `var identifier [len]type`

```go
package main  
import "fmt"  
func main() {  
   var x [5]int  
   var i, j int  
   for i = 0; i < 5; i++ {  
      x[i] = i + 10  
   }  
   for j = 0; j < 5; j++ {  
      fmt.Printf("Element[%d] = %d\n", j, x[j])  
   }  
}
/*
Ouput
Element[0] = 10
Element[1] = 11
Element[2] = 12
Element[3] = 13
Element[4] = 14
*/
```

---

### Multi Dimensional Arrays

- list of one-dimensional arrays
- Syntax `var arrayName [x][y]variable_type`

```go
// Initalizing Two-Dimensional Arrays
a = [2][3]int{    
   {2, 4, 6} ,   /*  initializers for row indexed by 0 */  
   {8, 10, 12} ,   /*  initializers for row indexed by 1 */  
}
// Accessing Two-Dimensional Arrays
int val = a[1][2]
```

```go
package main  
import "fmt"  
func main() {  
   /* an array with 3 rows and 3 columns*/  
   var a = [3][3]int{ {1,2,3}, {4,5,6}, {7,8,9}}  
   var i, j int  
   /* output each array element's value */  
   for  i = 0; i < 3; i++ {  
      for j = 0; j < 3; j++ {  
         fmt.Print(a[i][j] )  
      }  
      fmt.Println()  
   }  
}
/* 
Output 
123
456
789
*/
```

---

### Shorthand declaration of array

- Syntax  `array_name := [length]Type{item1,item2,item3,..,itemN}`

```go
package main 
  
import "fmt"
  
func main() { 
  
// Shorthand declaration of array 
arr:= [4]string{"A", "B", "C", "D"} 
  
// Accessing the elements of  
// the array Using for loop 
fmt.Println("Elements of the array:") 
  
for i:= 0; i < 3; i++{ 
fmt.Println(arr[i]) 
} 
  
}
```

---

### Important observations about Arrays

1. If an array is not initialized explicitly, then the default value if this array is 0
2. to find the length of array using len() method 
3. if ellipsis "..." become visible at the place of length, then the length of the array is determined by the initialized elements 

```go
package main 
  
import "fmt"
  
func main() { 
      
// Creating an array whose size is determined  
// by the number of elements present in it 
// Using ellipsis 
myarray:= [...]string{"A", "B", "C", 
                    "D", "E"} 
  
fmt.Println("Elements of the array: ", myarray) 
  
// Length of the array 
// is determine by  
// Using len() method 
fmt.Println("Length of the array is:", len(myarray)) 
}
```

4.  iterating over the range of the elements of the array is possible 

```go
package main 
  
import "fmt"
  
func main() { 
      
// Creating an array whose size 
// is represented by the ellipsis 
myarray:= [...]int{29, 79, 49, 39, 
                   20, 49, 48, 49} 
  
// Iterate array using for loop 
for x:=0; x < len(myarray); x++{ 
fmt.Printf("%d\n", myarray[x]) 
} 
}
```

5.  an array is of value type not of reference type; when array is assigned to a new variable, then the changes made in the new variable do not affect the original array. 

```go
package main 
  
import "fmt"
  
func main() { 
      
// Creating an array whose size  
// is represented by the ellipsis 
my_array:= [...]int{100, 200, 300, 400, 500} 
fmt.Println("Original array(Before):", my_array) 
  
// Creating a new variable  
// and initialize with my_array 
new_array := my_array 
  
fmt.Println("New array(before):", new_array) 
  
// Change the value at index 0 to 500 
new_array[0] = 500 
  
fmt.Println("New array(After):", new_array) 
  
fmt.Println("Original array(After):", my_array) 
}
```

6.  if the element type of the array is comparable then the array type is also comparable. So directly compare two arrays using == operator 

```go
package main 
  
import "fmt"
  
func main() { 
  
// Arrays     
arr1:= [3]int{9,7,6} 
arr2:= [...]int{9,7,6} 
arr3:= [3]int{9,5,3} 
  
// Comparing arrays using == operator 
fmt.Println(arr1==arr2) // true
fmt.Println(arr2==arr3) // false 
fmt.Println(arr1==arr3) // false 
  
// This will give and error because the  
// type of arr1 and arr4 is a mismatch  
/* 
arr4:= [4]int{9,7,6} 
fmt.Println(arr1==arr4) 
*/
}
```

---

### Copying one array into another array

- two ways :
    - assign a new variable by value → changes made to the original array wont be reflected to the copy array
    - assign a new variable by reference → changes made to the original array will be reflected to the copy array

```go
/* Syntax */
// creating a copy of an array by value
arr := arr1
// creating a copy of an array by reference 
arr := &arr1
```

```go
package main 
  
import "fmt"
  
func main() { 
  
    // Creating and initializing an array 
    // Using shorthand declaration 
    my_arr1 := [5]string{"Scala", "Perl", "Java", "Python", "Go"} 
  
    // Copying the array into new variable 
    // Here, the elements are passed by value 
    my_arr2 := my_arr1 
  
    fmt.Println("Array_1: ", my_arr1) 
    fmt.Println("Array_2:", my_arr2) 
  
    my_arr1[0] = "C++"
  
    // Here, when we copy an array 
    // into another array by value 
    // then the changes made in original 
    // array do not reflect in the 
    // copy of that array 
    fmt.Println("\nArray_1: ", my_arr1) 
    fmt.Println("Array_2: ", my_arr2) 
}
```

```go
package main 
  
import "fmt"
  
func main() { 
  
    // Creating and initializing an array 
    // Using shorthand declaration 
    my_arr1 := [6]int{12, 456, 67, 65, 34, 34} 
  
    // Copying the array into new variable 
    // Here, the elements are passed by reference 
    my_arr2 := &my_arr1 
  
    fmt.Println("Array_1: ", my_arr1) 
    fmt.Println("Array_2:", *my_arr2) 
  
    my_arr1[5] = 1000000 
  
    // Here, when we copy an array  
    // into another array by reference 
    // then the changes made in original  
    // array will reflect in the 
    // copy of that array 
    fmt.Println("\nArray_1: ", my_arr1) 
    fmt.Println("Array_2:", *my_arr2) 
}
```

---

### Pass an Array to a Function

```go
// For sized array
func function_name(variable_name [size]type){
// Code
}
```

```go
// Example 
package main
 
import "fmt"
 
// This function accept 
// an array as an argument
func myfun(a [6]int, size int) int {
    var k, val, r int
 
    for k = 0; k < size; k++ {
        val += a[k]
    }
 
    r = val / size
    return r
}
 
// Main function
func main() {
 
    // Creating and initializing an array
    var arr = [6]int{67, 59, 29, 35, 4, 34}
    var res int
 
    // Passing an array as an argumnet
    res = myfun(arr, 6)
    fmt.Printf("Final result is: %d ", res)
}
/* 
Output 
Final result is: 38
*/
```

---
