# Go Structs 
### Structs 
- also called as structure 
- user defined type (composite in nature)
- allows to group/combine items of possibly different types into a single  type. 
- can represent real-world entity which has some set of properties/fields 
- compared as a classes in object-oriented programming.
- termed as a lightweight class that doesnot support inheritance but supports composition
```go 
type Address struct {
  name string 
  street string 
  city string 
  state string 
  Pincode int 
}
```
The above code can be made compact by combining the various fields of the same type. 
```go 
type Address struct {
    name, street, city, state string
    Pincode int
}
```
- Syntax for declaring structure `var a Address` 
- variable of a type Address which is by default set to zero. 
- by default in a struct all the fields are set to their corresponding zero values ( text to "", int to 0).
- structs can also be initalized through struct literals like `var a = Address{"A","B","C","D"}`

---
