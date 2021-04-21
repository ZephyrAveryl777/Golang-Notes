---
title: MAPS
created: '2021-04-21T10:47:41.367Z'
modified: '2021-04-21T11:57:37.857Z'
---

# MAPS

- An unordered collection of key value pair.

- Also known as a dictionary or a hash table or as an associative array.

- Used in searching for a value with the help of its associated key.

- The type of keys and type of values must be of the same type, different types of keys and values in the same maps are not allowed. But the type of key and the type values can differ.

**How to creating and initializing Maps?**
*1*

- // An Empty map
        map[Key_Type]Value_Type{}

- // Map with key-value pair
        map[Key_Type]Value_Type{key1: value1, ..., keyN: valueN}

- Example

var mymap map[int]string

*2*

- Using make function
Syntax:

  make(map[Key_Type]Value_Type, initial_Capacity)
  make(map[Key_Type]Value_Type)
```go
// Go program to illustrate how to
// create and initialize a map
// Using make() function
package main

import "fmt"

func main() {

	// Creating a map
	// Using make() function
	var My_map = make(map[float64]string)
	fmt.Println(My_map)

	// As we already know that make() function
	// always returns a map which is initialized
	// So, we can add values in it
	My_map[1.3] = "Rohit"
	My_map[1.5] = "Sumit"
	fmt.Println(My_map)
}
/*
Output:

map[]
map[1.3:Rohit 1.5:Sumit]
*/
```

**How to iterate over a map?**
- You can iterate a map using the range for loop

```go
// Go program to illustrate how
// to iterate the map using for
// rang loop

package main

import "fmt"

// Main function
func main() {

	// Creating and initializing a map
	m_a_p := map[int]string{

		90: "Dog",
		91: "Cat",
		92: "Cow",
		93: "Bird",
		94: "Rabbit",
	}

	// Iterating map using for rang loop
	for id, pet := range m_a_p {

		fmt.Println(id, pet)
	}
}

/*
Output:

90 Dog
91 Cat
92 Cow
93 Bird
94 Rabbit
*/
```

**How to add key-value pairs in the map?**

```go
// Go program to illustrate how to add
// a key-value pair in the map using
// make() function
package main

import "fmt"

// Main function
func main() {

	// Creating and initializing a map
	m_a_p := map[int]string{
		90: "Dog",
		91: "Cat",
		92: "Cow",
		93: "Bird",
		94: "Rabbit",
	}

	fmt.Println("Original map: ", m_a_p)

	// Adding new key-value pairs in the map
	m_a_p[95] = "Parrot"
	m_a_p[96] = "Crow"
	fmt.Println("Map after adding new key-value pair:\n", m_a_p)

	// Updating values of the map
	m_a_p[91] = "PIG"
	m_a_p[93] = "DONKEY"
	fmt.Println("\nMap after updating values of the map:\n", m_a_p)
}

/*
Output:

Original map:  map[90:Dog 91:Cat 92:Cow 93:Bird 94:Rabbit]
Map after adding new key-value pair:
 map[90:Dog 91:Cat 92:Cow 93:Bird 94:Rabbit 95:Parrot 96:Crow]

Map after updating values of the map:
 map[90:Dog 91:PIG 92:Cow 93:DONKEY 94:Rabbit 95:Parrot 96:Crow]
 */
```

**How to retrieve a value related to a key in the maps?**

```go
// Go program to illustrate how to
// retrieve the value of the key

package main

import "fmt"

// Main function
func main() {

	// Creating and initializing a map
	m_a_p := map[int]string{
		90: "Dog",
		91: "Cat",
		92: "Cow",
		93: "Bird",
		94: "Rabbit",
	}
	fmt.Println("Original map: ", m_a_p)

	// Retrieving values with the help of keys
	value_1 := m_a_p[90]
	value_2 := m_a_p[93]
	fmt.Println("Value of key[90]: ", value_1)
	fmt.Println("Value of key[93]: ", value_2)
}

/*
Output:

Original map:  map[90:Dog 91:Cat 92:Cow 93:Bird 94:Rabbit]
Value of key[90]:  Dog
Value of key[93]:  Bird
*/
```
**How to check the existence of the key in the map?**

// With value
// It will gives the value and check result


- value, check_variable_name:= map_name[key]

or

// Without value using the blank identifier
// It will only give check result


- _, check_variable_name:= map_name[key]

```go
// Go program to illustrate how to
// check the key is available or not

package main

import "fmt"

// Main function
func main() {

	// Creating and initializing a map
	m_a_p := map[int]string{
		90: "Dog",
		91: "Cat",
		92: "Cow",
		93: "Bird",
		94: "Rabbit",
	}

	fmt.Println("Original map: ", m_a_p)

	// Checking the key is available
	// or not in the m_a_p map
	pet_name, ok := m_a_p[90]
	fmt.Println("\nKey present or not:", ok)
	fmt.Println("Value:", pet_name)

	// Using blank identifier
	_, ok1 := m_a_p[92]
	fmt.Println("\nKey present or not:", ok1)
}

/*
Output:

Original map:  map[90:Dog 91:Cat 92:Cow 93:Bird 94:Rabbit]

Key present or not: true
Value: Dog

Key present or not: true
*/
```

**How to delete key from the map?**

- Syntax:

     delete(map_name, key)
```go
// Go program to illustrate how to delete a key

package main

import "fmt"

// Main function
func main() {

	// Creating and initializing a map
	m_a_p := map[int]string{
		90: "Dog",
		91: "Cat",
		92: "Cow",
		93: "Bird",
		94: "Rabbit",
	}

	fmt.Println("Original map: ", m_a_p)

	// Deleting keys
	// Using delete function
	delete(m_a_p, 90)
	delete(m_a_p, 93)

	fmt.Println("Map after deletion: ", m_a_p)
}

/*
Output:

Original map:  map[90:Dog 91:Cat 92:Cow 93:Bird 94:Rabbit]
Map after deletion:  map[91:Cat 92:Cow 94:Rabbit]
*/
```
