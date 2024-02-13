# Data Types
In Golang, data types define the type of data that a variable can hold.

1. **Numeric Types**:
   - Integers (`int`, `int8`, `int16`, `int32`, `int64`): Signed integers represent whole numbers, while the number after `int` specifies the number of bits used to represent the integer.
   - Unsigned Integers (`uint`, `uint8`, `uint16`, `uint32`, `uint64`): Unsigned integers represent only non-negative whole numbers.
   - Floating-point Numbers (`float32`, `float64`): Represent numbers with fractional parts or numbers that are too large or too small to be represented as integers.


   ```go
   package main

   import (
       "fmt"
   )

   func main() {
       var x int = 10
       var y float64 = 3.14

       fmt.Println("Integer:", x)
       fmt.Println("Float:", y)
   }
   ```

   Output:
   ```
   Integer: 10
   Float: 3.14
   ```

![](/image/Screenshot_1.jpg)
![](/image/Screenshot_2.jpg)


   #### Integer Types:
```go
package main

import "fmt"

func main() {
    var x int = 10
    var y int8 = 20
    var z uint = 30

    fmt.Println("Int:", x)
    fmt.Println("Int8:", y)
    fmt.Println("Uint:", z)
}
```

Output:
```
Int: 10
Int8: 20
Uint: 30
```

![](/image/Screenshot_3.jpg)

![](/image/Screenshot_4.jpg)


#### Floating-Point Types:
```go
package main

import "fmt"

func main() {
    var x float32 = 3.14
    var y float64 = 6.283185

    fmt.Println("Float32:", x)
    fmt.Println("Float64:", y)
}
```

Output:
```
Float32: 3.14
Float64: 6.283185
```

![](/image/Screenshot_5.jpg)

![](/image/Screenshot_6.jpg)


2. **Boolean Type**:
   - **bool**: Represents true or false values.

   ```go
   package main

   import (
       "fmt"
   )

   func main() {
       var isTrue bool = true
       var isFalse bool = false

       fmt.Println("True:", isTrue)
       fmt.Println("False:", isFalse)
   }
   ```

   Output:
   ```
   True: true
   False: false
   ```

![](/image/Screenshot_7.jpg)

![](/image/Screenshot_8.jpg)


3. **String Type**:
   - **string**: Represents a sequence of characters.

   ```go
   package main

   import (
       "fmt"
   )

   func main() {
       var message string = "Hello Saklain!"

       fmt.Println(message)
   }
   ```

   Output:
   ```
   Hello Saklain!
   ```

   ![](/image/Screenshot_9.jpg)

   ![](/image/Screenshot_10.jpg)


4. ***Composite Types***:
   
 **Array**:
   - An array in Go is a fixed-size collection of elements of the same type.
   - The size of an array is part of its type, meaning the length of the array cannot be changed after it is declared.
   - Arrays are declared using the syntax `[size]type`, where `size` specifies the number of elements and `type` specifies the type of each element.

 **Slice**:
   - A slice is a dynamic-size view into the elements of an array.
   - Unlike arrays, slices do not have a fixed size and can grow or shrink dynamically.
   - Slices are created using the `make()` function or by slicing an existing array or slice using the syntax `array[start:end]`.
   - Slices are widely used in Go for their flexibility and ease of use in handling collections of data.

 **Map**:
   - A map is a collection of key-value pairs, where each key is unique.
   - Maps provide fast lookups of values based on keys.
   - Maps are declared using the syntax `map[keyType]valueType`, where `keyType` and `valueType` specify the types of keys and values, respectively.
   - Maps are commonly used in Go for associative data structures, such as dictionaries and hash tables.

 **Struct**:
   - A struct is a user-defined composite type that groups together zero or more fields of any type.
   - Fields within a struct can be of different types, allowing for the creation of complex data structures.
   - Structs are declared using the `type` keyword followed by a struct definition, which specifies the names and types of the fields.
   - Structs are used in Go to represent objects with multiple properties or attributes, similar to classes in object-oriented programming languages.


   ```go
   package main

   import "fmt"

   func main() {
       // Array
       var arr [3]int = [3]int{1, 2, 3}

       // Slice
       var slice []int = []int{4, 5, 6}

       // Map
       var m map[string]int = map[string]int{"a": 7, "b": 8, "c": 9}

       // Struct
       type Person struct {
           Name string
           Age  int
       }
       var p Person = Person{Name: "Saklain", Age: 21}

       fmt.Println("Array:", arr)
       fmt.Println("Slice:", slice)
       fmt.Println("Map:", m)
       fmt.Println("Struct:", p)
   }
   ```

   Output:
   ```
   Array: [1 2 3]
   Slice: [4 5 6]
   Map: map[a:7 b:8 c:9]
   Struct: {Saklain 21}
   ```

![](/image/Screenshot_11.jpg)

![](/image/Screenshot_12.jpg)


### 1. Arrays
```go
package main

import "fmt"

func main() {
    // Declaring and initializing an array
    var arr [3]int = [3]int{1, 2, 3}

    // Accessing elements of the array
    fmt.Println("Array:", arr)
    fmt.Println("First element:", arr[0])
    fmt.Println("Second element:", arr[1])
    fmt.Println("Third element:", arr[2])
}
```

Output:
```
Array: [1 2 3]
First element: 1
Second element: 2
Third element: 3
```

![](/image/Screenshot_13.jpg)
![](/image/Screenshot_14.jpg)

### 2. Slices
```go
package main

import "fmt"

func main() {
    // Declaring and initializing a slice
    var slice []int = []int{4, 5, 6}

    // Modifying slice elements
    slice[0] = 7

    // Appending to slice
    slice = append(slice, 8)

    // Accessing elements of the slice
    fmt.Println("Slice:", slice)
    fmt.Println("First element:", slice[0])
    fmt.Println("Second element:", slice[1])
    fmt.Println("Third element:", slice[2])
    fmt.Println("Fourth element:", slice[3])
}
```

Output:
```
Slice: [7 5 6 8]
First element: 7
Second element: 5
Third element: 6
Fourth element: 8
```

![](/image/Screenshot_15.jpg)
![](/image/Screenshot_16.jpg)

### 3. Maps
```go
package main

import "fmt"

func main() {
    // Declaring and initializing a map
    var m map[string]int = map[string]int{"a": 7, "b": 8, "c": 9}

    // Accessing map elements
    fmt.Println("Map:", m)
    fmt.Println("Value for key 'a':", m["a"])
    fmt.Println("Value for key 'b':", m["b"])
    fmt.Println("Value for key 'c':", m["c"])
}
```

Output:
```
Map: map[a:7 b:8 c:9]
Value for key 'a': 7
Value for key 'b': 8
Value for key 'c': 9
```

![](/image/Screenshot_17.jpg)
![](/image/Screenshot_18.jpg)

### 4. Structs
```go
package main

import "fmt"

func main() {
    // Defining a struct
    type Person struct {
        Name string
        Age  int
    }

    // Creating an instance of struct
    var p Person = Person{Name: "Saklain", Age: 21}

    // Accessing struct fields
    fmt.Println("Name:", p.Name)
    fmt.Println("Age:", p.Age)
}
```

Output:
```
Name: Saklain
Age: 21
```

![](/image/Screenshot_19.jpg)
![](/image/Screenshot_20.jpg)
