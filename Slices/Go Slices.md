# Go Slices

Learned: Mar 1, 2021 8:39 PM

### Slice

- dynamically-sized, segmented view of an underlying array
- segment can be the entire array or a subset of an array
- define the subset of an array by indicating the start and end index
- Syntax   `[]T or []T{} or []T{value1,value2,value3,...,valueN}` `var  my_slice[]int T is th type of the elements.`

```go
 package main  
import (  
   "fmt"  
)  
func main() {  
   odd := [6]int{2, 4, 6, 8, 10, 12}  
   var s []int = odd[1:4]  
   fmt.Println(s)  
}
// Output : [4 6 8]
```

- Slice is like reference to an array, does not store data
- If we change the elements of an array, it will also modify the underlying array.
- If other slice is referencing the same underlying array, their value will also be changed.

```go
package main  
import "fmt"  
func main() {  
   names := [4]string{  
      "John",  
      "Jim",  
      "Jack",  
      "jen",  
   }  
   fmt.Println(names)  
   slice1 := names[0:2]  
   slice2 := names[1:3]  
   fmt.Println(slice1, slice2)  
   slice2[0] = "ZZZ"  
   fmt.Println(slice1, slice2)  
   fmt.Println(names)  
}
/* 
Output 
[John Jim Jack jen]
[John Jim] [Jim Jack]
[John ZZZ] [ZZZ Jack]
[John ZZZ Jack jen]
*/
```

- illustration of slice

    ![Go%20Slices%20437ad614456649eea86a2373accf7392/Untitled.png](Go%20Slices%20437ad614456649eea86a2373accf7392/Untitled.png)

---

### Create and initialize a Slice

- using slice literal:
    - same like array literal
    - no need to specify the size of the slice in the square braces []
    - Syntax: `var my_slice_1 = []string{"A","B","C"}`
    - when creating a slice using string literal, first create an array after that return a slice reference to it.

    ```go
    package main
     
    import "fmt"
     
    func main() {
     
        // Creating a slice
        // using the var keyword
        var my_slice_1 = []string{"A", "B", "C"}
     
        fmt.Println("My Slice 1:", my_slice_1)
     
        // Creating a slice
        //using shorthand declaration
        my_slice_2 := []int{12, 45, 67, 56, 43, 34, 45}
        fmt.Println("My Slice 2:", my_slice_2)
    }
    /* 
    Output
    My Slice 1: [A B C]
    My Slice 2: [12 45 67 56 43 34 45] 
    */
    ```

- Using an Array :
    - create a slice from the given array.
    - specify the lower and upper bound, as slice takes elements from array,
    - Syntax : `array_name[low:high]`
    - lower bound by default is 0 and upper bound is total number of elements present in array

```go
package main
 
import "fmt"
 
func main() {
 
    // Creating an array
    arr := [4]string{"A", "B", "C", "D"}
 
    // Creating slices from the given array
    var my_slice_1 = arr[1:2]
    my_slice_2 := arr[0:]
    my_slice_3 := arr[:2]
    my_slice_4 := arr[:]
 
    // Display the result
    fmt.Println("My Array: ", arr)
    fmt.Println("My Slice 1: ", my_slice_1)
    fmt.Println("My Slice 2: ", my_slice_2)
    fmt.Println("My Slice 3: ", my_slice_3)
    fmt.Println("My Slice 4: ", my_slice_4)
}
/* 
Output
My Array:  [A B C D]
My Slice 1:  [B]
My Slice 2:  [A B C D]
My Slice 3:  [A  B]
My Slice 4:  [A B C D]
```

- Using already existing Slice :
    - create slice from given slice
    - specify lower and upper bound
    - Syntax : `slice_name[low:high]`

```go
package main
 
import "fmt"
 
func main() {
 
    // Creating s slice
    oRignAl_slice := []int{90, 60, 40, 50,
        34, 49, 30}
 
    // Creating slices from the given slice
    var my_slice_1 = oRignAl_slice[1:5]
    my_slice_2 := oRignAl_slice[0:]
    my_slice_3 := oRignAl_slice[:6]
    my_slice_4 := oRignAl_slice[:]
    my_slice_5 := my_slice_3[2:4]
 
    // Display the result
    fmt.Println("Original Slice:", oRignAl_slice)
    fmt.Println("New Slice 1:", my_slice_1)
    fmt.Println("New Slice 2:", my_slice_2)
    fmt.Println("New Slice 3:", my_slice_3)
    fmt.Println("New Slice 4:", my_slice_4)
    fmt.Println("New Slice 5:", my_slice_5)
}
/*
Ouput 
Original Slice: [90 60 40 50 34 49 30]
New Slice 1: [60 40 50 34]
New Slice 2: [90 60 40 50 34 49 30]
New Slice 3: [90 60 40 50 34 49]
New Slice 4: [90 60 40 50 34 49 30]
New Slice 5: [40 50]
*/ 
```

- Using make() function :
    - this function takes three parameters i.e type, length and capacity (capacity is optional)
    - make() function is used to create empty slice generally
    - Syntax:  `func make([]T, len, cap)[]T`

```go
package main
 
import "fmt"
 
func main() {
 
    // Creating an array of size 7
    // and slice this array  till 4
    // and return the reference of the slice
    // Using make function
    var my_slice_1 = make([]int, 4, 7)
    fmt.Printf("Slice 1 = %v, \nlength = %d, \ncapacity = %d\n",
                   my_slice_1, len(my_slice_1), cap(my_slice_1))
 
    // Creating another array of size 7
    // and return the reference of the slice
    // Using make function
    var my_slice_2 = make([]int, 7)
    fmt.Printf("Slice 2 = %v, \nlength = %d, \ncapacity = %d\n",
                   my_slice_2, len(my_slice_2), cap(my_slice_2))
     
}
/* Output
Slice 1 = [0 0 0 0], 
length = 4, 
capacity = 7
Slice 2 = [0 0 0 0 0 0 0], 
length = 7, 
capacity = 7
*/
```

---

### Iterate over a slice

- Using for loop :  simplest way to iterate slice

```go
package main
 
import "fmt"
 
func main() {
 
    // Creating a slice
    myslice := []string{"This", "is", "the", "tutorial",
        "of", "Go", "language"}
 
    // Iterate using for loop
    for e := 0; e < len(myslice); e++ {
        fmt.Println(myslice[e])
    }
}
/* 
Output 
This
is
the
tutorial
of
Go
language
*/
```

- Using range in for loop :
    - iterate over a slice using range in the for loop
    - using range, can get index and the element value

```go
package main
 
import "fmt"
 
func main() {
 
    // Creating a slice
    myslice := []string{"This", "is", "the", "tutorial",
                                 "of", "Go", "language"}
 
    // Iterate slice
    // using range in for loop
    for index, ele := range myslice {
        fmt.Printf("Index = %d and element = %s\n", index+3, ele)
    }
}
/* 
Output
Index = 3 and element = This
Index = 4 and element = is
Index = 5 and element = the
Index = 6 and element = tutorial
Index = 7 and element = of
Index = 8 and element = Go
Index = 9 and element = language
*/
```

- Using a blank identifier in for loop :
    - using blank space (_) in the place of index variables  in the range for loop.

```go
package main
 
import "fmt"
 
func main() {
 
    // Creating a slice
    myslice := []string{"This", "is", "the",
        "tutorial", "of", "Go", "language"}
 
    // Iterate slice
    // using range in for loop
    // without index
    for _, ele := range myslice {
        fmt.Printf("Element = %s\n", ele)
    }
}
/*
Ouptut 
Element = This
Element = is
Element = the
Element = tutorial
Element = of
Element = Go
Element = language
*/
```

---

### Important points about Slice

- Zero value slice :
    - create a nil slice that does not contain any element in it.
    - capacity and the length of the slice is 0.
    - Nil slice does not contain an array reference

```go
package main
 
import "fmt"
 
func main() {
 
    // Creating a zero value slice
    var myslice []string
    fmt.Printf("Length = %d\n", len(myslice))
    fmt.Printf("Capacity = %d ", cap(myslice))
 
}
/* 
Output
Length = 0
Capacity = 0
*/
```

- Modifying Slice :  any changes in the slice, then it will also reflect in the array.

```go
package main
 
import "fmt"
 
func main() {
 
    // Creating a zero value slice
    arr := [6]int{55, 66, 77, 88, 99, 22}
    slc := arr[0:4]
 
    // Before modifying
 
    fmt.Println("Original_Array: ", arr)
    fmt.Println("Original_Slice: ", slc)
 
    // After modification
    slc[0] = 100
    slc[1] = 1000
    slc[2] = 1000
 
    fmt.Println("\nNew_Array: ", arr)
    fmt.Println("New_Slice: ", slc)
}
/* 
Ouput
Original_Array:  [55 66 77 88 99 22]
Original_Slice:  [55 66 77 88]

New_Array:  [100 1000 1000 88 99 22]
New_Slice:  [100 1000 1000 88]
*/
```

- Comparison of Slice:
    - use  `==`  operator to check the given slice is nill or not.
    - if try to compare two slice with the help of `==` operator then it will give an error.

```go
package main
 
import "fmt"
 
func main() {
 
    // creating slices
    s1 := []int{12, 34, 56}
    var s2 []int
 
    // If you try to run this commented
    // code compiler will give an error
    /*s3:= []int{23, 45, 66}
      fmt.Println(s1==s3)
    */
 
    // Checking if the given slice is nil or not
    fmt.Println(s1 == nil)
    fmt.Println(s2 == nil)
}
/* 
Output
false 
true
*/
```

- to compare two slices, use range for loop to match each element or use  DeepEqual function
- Multi-Dimensional Slice does not contain the size.

```go
package main
 
import "fmt"
 
func main() {
 
    // Creating multi-dimensional slice
    s1 := [][]int{{12, 34},
        {56, 47},
        {29, 40},
        {46, 78},
    }
 
    // Accessing multi-dimensional slice
    fmt.Println("Slice 1 : ", s1)
 
    // Creating multi-dimensional slice
    s2 := [][]string{
        []string{"A", "a"},
        []string{"B", "b"},
        []string{"C", "c"},
    }
 
    // Accessing multi-dimensional slice
    fmt.Println("Slice 2 : ", s2)
 
}
/*
Output
Slice 1 :  [[12 34] [56 47] [29 40] [46 78]]
Slice 2 :  [[A a] [B b] [C c]]
*/
```

- **Sorting of Slice** :
    - standard library of Go provides sort package which contains different types of sorting methods for sorting the slice of ints, float64, strings.

```go
package main
 
import (
    "fmt"
    "sort"
)
 
func main() {
 
    // Creating Slice
    slc1 := []string{"Python", "Java", "C#", "Go", "Ruby"}
    slc2 := []int{45, 67, 23, 90, 33, 21, 56, 78, 89}
 
    fmt.Println("Before sorting:")
    fmt.Println("Slice 1: ", slc1)
    fmt.Println("Slice 2: ", slc2)
 
    // Performing sort operation on the
    // slice using sort function
    sort.Strings(slc1)
    sort.Ints(slc2)
 
    fmt.Println("\nAfter sorting:")
    fmt.Println("Slice 1: ", slc1)
    fmt.Println("Slice 2: ", slc2)
 
}
/*
Output
Before sorting:
Slice 1:  [Python Java C# Go Ruby]
Slice 2:  [45 67 23 90 33 21 56 78 89]

After sorting:
Slice 1:  [C# Go Java Python Ruby]
Slice 2:  [21 23 33 45 56 67 78 89 90]
*/
```

---

### Slice Composite Literal in Go

- slice is a composite data type similar to array
- main difference is that it(slice) can vary in size dynamically.
- Composite literals are used to construct the values for arrays, structs, slices, and maps
- Each time they are evaluated, it will create new value.

```go
package main 
  
import "fmt"
  
func main() { 
  
    // Slice with composite literal 
    // Slice allows you to group together 
    // the values of the same type  
    // here type of values is int 
    s1 := []int{23, 56, 89, 34} 
      
    // displaying the values 
    fmt.Println(s1) 
}
/* 
Ouput
[23 56 89 34]
*/
```

---
