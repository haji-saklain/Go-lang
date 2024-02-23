
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

func main() {
	fmt.Println("Insert Text")
	in := bufio.NewReader(os.Stdin)
	s, _ := in.ReadString('\n')
	s = strings.TrimSpace(s)
	s = strings.ToUpper(s)
	fmt.Println(s + "!")
}
```

```go
Insert Text
hi, my name is saklain
HI, MY NAME IS SAKLAIN!
```

This Go code reads a string from the standard input (keyboard input), converts it to uppercase, trims any leading or trailing whitespace, and then prints it with an exclamation mark.

Here's a step-by-step explanation of the code:

# Arrays 
```go
package main

import "fmt"

func main() {
    // Declaring an array of strings with length 3
    var arr [3]string
    fmt.Println(arr) // Output: [  ]

    // Initializing the array with values
    arr = [3]string{"Coffee", "Espresso", "Cappuccino"}
    fmt.Println(arr) // Output: [Coffee Espresso Cappuccino]

    // Accessing an element of the array
    fmt.Println(arr[1]) // Output: Espresso

    // Modifying an element of the array
    arr[1] = "Chai Tea"
    fmt.Println(arr) // Output: [Coffee Chai Tea Cappuccino]

    // Creating a new array and copying values from the original array
    arr2 := arr
    arr2[2] = "Chai Latte"
    
    // Printing both arrays
    fmt.Println(arr, arr2) // Output: [Coffee Chai Tea Cappuccino] [Coffee Chai Tea Chai Latte]
}
```

**Output:**
```
[  ]
[Coffee Espresso Cappuccino]
Espresso
[Coffee Chai Tea Cappuccino]
[Coffee Chai Tea Cappuccino] [Coffee Chai Tea Chai Latte]
```

**Explanation:**

1. **Array Declaration and Initialization:**
   - An array `arr` of type string with a length of 3 is declared.
   - Initially, since no values are assigned, the elements are initialized with their zero values, which for strings is an empty string.
   - The array is printed, resulting in `[]`.

2. **Array Initialization with Values:**
   - The array `arr` is initialized with specific string values: "Coffee", "Espresso", and "Cappuccino".
   - The array is printed, resulting in `[Coffee Espresso Cappuccino]`.

3. **Accessing Elements:**
   - The second element of the array (index 1), "Espresso", is accessed and printed.

4. **Modifying Elements:**
   - The second element of the array is modified from "Espresso" to "Chai Tea".
   - The modified array is printed, resulting in `[Coffee Chai Tea Cappuccino]`.

5. **Copying Arrays:**
   - A new array `arr2` is created, and the values of `arr` are copied into it.
   - The third element of `arr2` is modified from "Cappuccino" to "Chai Latte".
   - Both `arr` and `arr2` are printed, showing the modification only in `arr2`.

# Slices 

```go
package main

import (
	"fmt"
	"slices"
)

func main() {
	var s []string
	fmt.Println(s) // Output: []

	s = []string{"Coffee", "Espresso", "Cappuccino"}
	fmt.Println(s) // Output: [Coffee Espresso Cappuccino]

	fmt.Println(s[1]) // Output: Espresso
	s[1] = "Chai Tea"
	fmt.Println(s) // Output: [Coffee Chai Tea Cappuccino]

	s = append(s, "Hot Chocolate", "Hot Tea")
	fmt.Println(s) // Output: [Coffee Chai Tea Cappuccino Hot Chocolate Hot Tea]

	s = slices.Delete(s, 1, 2)
	fmt.Println(s) // Output: [Coffee Cappuccino Hot Chocolate Hot Tea]

	s2 := s

	s[2] = "Chai Latte"

	fmt.Println(s, s2) // Output: [Coffee Cappuccino Chai Latte Hot Chocolate Hot Tea] [Coffee Cappuccino Chai Latte Hot Chocolate Hot Tea]
}
```

Explanation:

1. The program imports a custom package named "slices" that contains a function named `Delete`.

2. In the `main` function:
   - An empty slice of strings `s` is declared and printed (`[]`).
   - The slice `s` is initialized with three string elements: "Coffee", "Espresso", and "Cappuccino", and then printed.
   - The second element of slice `s` (index 1) is printed, which is "Espresso". Then, it is replaced with "Chai Tea", and the modified slice is printed.
   - Two more string elements, "Hot Chocolate" and "Hot Tea", are appended to the slice `s`, and the modified slice is printed.
   - The `Delete` function from the "slices" package is called to delete elements at indices 1 and 2 from slice `s`, and the modified slice is printed.
   - A new slice `s2` is declared and assigned the value of slice `s`.
   - The third element of slice `s` (index 2) is modified to "Chai Latte".
   - Both slices `s` and `s2` are printed to observe the change. Both slices reflect the modification made to slice `s`.

Output:
```
[]
[Coffee Espresso Cappuccino]
Espresso
[Coffee Chai Tea Cappuccino]
[Coffee Chai Tea Cappuccino Hot Chocolate Hot Tea]
[Coffee Cappuccino Hot Chocolate Hot Tea]
[Coffee Cappuccino Chai Latte Hot Chocolate Hot Tea] [Coffee Cappuccino Chai Latte Hot Chocolate Hot Tea]
```

This code shows different things you can do with slices in Go. Slices are like lists in other programming languages. You can do things like create them, change what's inside them, add new stuff to them, take things out of them, and copy them.
- It starts by creating a slice, which is like a list, and prints it out.
- Then, it changes something inside the slice and prints it again.
- After that, it adds something new to the slice and prints it again.
- Next, it removes something from the slice and prints it again.
- Finally, it copies the slice and prints both the original and the copy to show they are separate but have the same content.

# Maps

```go
package main

import (
	"fmt"
)

func main() {
	// Declare a map variable m with keys of type string and values of type slice of string
	var m map[string][]string
	fmt.Println("Initial map:", m) // Output: Initial map: map[]

	// Initialize map m with key-value pairs
	m = map[string][]string{
		"coffee": {"Coffee", "Espresso", "Cappuccino"},
		"tea":    {"Hot Tea", "Chai Tea", "Chai Latte"},
	}

	fmt.Println("Map after initialization:", m) // Output: Map after initialization: map[coffee:[Coffee Espresso Cappuccino] tea:[Hot Tea Chai Tea Chai Latte]]

	// Access and print the value associated with the key "coffee"
	fmt.Println("Values for 'coffee':", m["coffee"]) // Output: Values for 'coffee': [Coffee Espresso Cappuccino]

	// Delete the key-value pair with key "tea"
	delete(m, "tea")
	fmt.Println("Map after deletion:", m) // Output: Map after deletion: map[coffee:[Coffee Espresso Cappuccino]]

	// Add a new key-value pair to the map
	m["other"] = []string{"Hot Chocolate"}
	fmt.Println("Map after addition:", m) // Output: Map after addition: map[coffee:[Coffee Espresso Cappuccino] other:[Hot Chocolate]]

	// Accessing a non-existent key "tea"
	fmt.Println("Values for 'tea':", m["tea"]) // Output: Values for 'tea': []

	// Check if a key "tea" exists in the map
	v, ok := m["tea"]
	fmt.Println("Value for 'tea':", v, "Existence:", ok) // Output: Value for 'tea': [] Existence: false

	// Assigning map m to another map variable m2
	m2 := m
	// Modify the value associated with the key "coffee" in map m2
	m2["coffee"] = []string{"Coffee"}
	// Modify the value associated with the key "tea" in map m
	m["tea"] = []string{"Hot Tea"}

	fmt.Println("Map m after modification:", m)   // Output: Map m after modification: map[coffee:[Coffee] other:[Hot Chocolate] tea:[Hot Tea]]
	fmt.Println("Map m2 after modification:", m2) // Output: Map m2 after modification: map[coffee:[Coffee] other:[Hot Chocolate] tea:[Hot Tea]]
}
```

**Output:**

```
Initial map: map[]
Map after initialization: map[coffee:[Coffee Espresso Cappuccino] tea:[Hot Tea Chai Tea Chai Latte]]
Values for 'coffee': [Coffee Espresso Cappuccino]
Map after deletion: map[coffee:[Coffee Espresso Cappuccino]]
Map after addition: map[coffee:[Coffee Espresso Cappuccino] other:[Hot Chocolate]]
Values for 'tea': []
Value for 'tea': [] Existence: false
Map m after modification: map[coffee:[Coffee] other:[Hot Chocolate] tea:[Hot Tea]]
Map m2 after modification: map[coffee:[Coffee] other:[Hot Chocolate] tea:[Hot Tea]]
```

**Explanation:**
This program is about using maps in Go. A map is like a dictionary where each item has a key and a value. 

- At the beginning, a map called `m` is made, but it's empty. We print it out, so it shows nothing.
- Then, we add some key-value pairs to the map. The keys are words, and the values are lists of words.
- Next, we do different things with the map like getting items by their key, removing items, adding new items, and checking if a key exists.
- Finally, we show that if you copy a map into another one, they both point to the same information. So if you change something in one map, it changes in the other map too.

# Struct


```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

func main() {
	// Print initial message
	fmt.Println("Please select an option")
	fmt.Println("1) Print menu")

	// Read user input
	in := bufio.NewReader(os.Stdin)
	choice, _ := in.ReadString('\n')
	choice = strings.TrimSpace(choice) // We don't know what to do with this yet!

	// Define a struct for menu items
	type menuItem struct {
		name   string
		prices map[string]float64
	}

	// Define menu items with their respective prices
	menu := []menuItem{
		{name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
		{name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
	}

	// Print the menu
	fmt.Println(menu)
}
```


**Output**:

```
Please select an option
1) Print menu
[{Coffee map[large:1.95 medium:1.8 small:1.65]} {Espresso map[double:2.25 single:1.9 triple:2.55]}]
```


**Explanation**:

- The program starts by printing a message prompting the user to select an option and printing the option to print the menu.

- It then reads the user's input using `bufio.NewReader(os.Stdin)` to create a reader to read from standard input, and `ReadString('\n')` to read until the user presses Enter. The input is stored in the variable `choice`.

- `strings.TrimSpace(choice)` is used to remove any leading or trailing whitespace from the user's input. However, at this stage of the code, we haven't implemented what to do with the user's choice yet.

- A custom type `menuItem` is defined, which represents a menu item. It has two fields: `name` (string) representing the name of the item and `prices` (map[string]float64) representing the prices of the item for different sizes or options.

- An array `menu` of `menuItem` structs is defined, containing two menu items: "Coffee" and "Espresso", each with their respective prices for different options.

- Finally, the program prints the entire menu array.



# Variables

```go
package main

import "fmt"

func main() {
    // Declare a variable 'a' of type string and assign the value "foo" to it
    var a string
    a = "foo"

    // Print the value of variable 'a'
    fmt.Println(a)

    // Declare a variable 'b' of type int and assign the value 99 to it
    var b int = 99
    // Print the value of variable 'b'
    fmt.Println(b)

    // Declare a variable 'c' and let Go infer its type as bool, and assign the value true to it
    var c = true
    // Print the value of variable 'c'
    fmt.Println(c)

    // Declare a variable 'd' and let Go infer its type as float64, and assign the value 3.1415 to it
    d := 3.1415
    // Print the value of variable 'd'
    fmt.Println(d)

    // Convert the value of 'd' to an integer and assign it to variable 'e'
    var e int = int(d)
    // Print the value of variable 'e'
    fmt.Println(e)
}
```

**Output:**
```
foo
99
true
3.1415
3
```

**Explanation:**

1. In this Go program, we declare and initialize variables of different types and print their values.

2. `var a string` declares a variable `a` of type string. We assign the value "foo" to `a` using `a = "foo"`.

3. `fmt.Println(a)` prints the value of `a`, which is "foo".

4. `var b int = 99` declares a variable `b` of type int and assigns it the value 99.

5. `fmt.Println(b)` prints the value of `b`, which is 99.

6. `var c = true` declares a variable `c` without explicitly specifying its type. Go infers the type of `c` as bool based on the assigned value true.

7. `fmt.Println(c)` prints the value of `c`, which is true.

8. `d := 3.1415` declares a variable `d` and lets Go infer its type as float64. We assign the value 3.1415 to `d`.

9. `fmt.Println(d)` prints the value of `d`, which is 3.1415.

10. `var e int = int(d)` converts the value of `d` to an integer and assigns it to variable `e`.

11. `fmt.Println(e)` prints the value of `e`, which is the truncated integer part of the value stored in `d`, in this case, 3.







# Arithmetic Operations

This Go program demonstrates basic arithmetic operations such as addition, subtraction, multiplication, division, and modulus. It also showcases type conversion and comparison operators.

```go
package main

import "fmt"

func main() {
    // Declaring two integer variables
    a, b := 5, 2

    // Addition
    fmt.Println(a + b)

    // Subtraction
    fmt.Println(a - b)

    // Multiplication
    fmt.Println(a * b)

    // Integer division (result is an integer)
    fmt.Println(a / b)

    // Modulus (remainder of integer division)
    fmt.Println(a % b)

    // Float division (result is a floating-point number)
    fmt.Println(float32(a) / float32(b))

    // Comparison operators
    fmt.Println(a == b) // Equal to
    fmt.Println(a < b)  // Less than
    fmt.Println(a > b)  // Greater than
}
```

Output:
```
7
3
10
2
1
2.5
false
false
true
```

Explanation:
- The program begins by declaring two integer variables `a` and `b` with values 5 and 2, respectively.
- It then performs various arithmetic operations:
  - Addition (`a + b`): 5 + 2 = 7
  - Subtraction (`a - b`): 5 - 2 = 3
  - Multiplication (`a * b`): 5 * 2 = 10
  - Integer division (`a / b`): 5 / 2 = 2 (integer division truncates the decimal part)
  - Modulus (`a % b`): 5 % 2 = 1 (remainder of 5 divided by 2)
  - Float division (`float32(a) / float32(b)`): 5.0 / 2.0 = 2.5 (explicit type conversion to float32)
- Finally, it demonstrates comparison operators:
  - Equal to (`a == b`): 5 is not equal to 2, so it prints `false`
  - Less than (`a < b`): 5 is not less than 2, so it prints `false`
  - Greater than (`a > b`): 5 is greater than 2, so it prints `true`

 
# Constants
This Go program demonstrates the usage of constants and the `iota` identifier.

```go
package main

import "fmt"

func main() {
    // Constants with explicit types
    const a = 42
    const b float32 = 3

    // Assigning constants to variables with compatible types
    var i int = a
    fmt.Println(i)
    var f32 float32 = a
    fmt.Println(f32)

    // Assigning constant 'b' to variable 'f32'
    f32 = b
    fmt.Println(f32)

    // iota usage in constant declarations
    const c = iota
    fmt.Println(c)

    // Using iota in a const block
    const (
        d = 2 * 5
        e     // e = 2 * 5 (implicitly)
        f = iota  // f = 0
        g         // g = 1 (incremented from iota)
        h = 10 * iota  // h = 10 * 2
    )

    // Printing values of constants
    fmt.Println(d, e, f, g, h)
}
```

### Output

```
42
42
3
0
10 10 0 1 20
```

### Explanation

1. Constants `a` and `b` are declared with values `42` and `3` respectively. `a` is untyped, and `b` is explicitly typed as `float32`.
2. Constant `a` is assigned to variable `i` of type `int`, and `f32` of type `float32`. Go allows this because the values are compatible.
3. Constant `b` is assigned to variable `f32`.
4. The `iota` identifier is used to generate sequential integer values in a const block. In this case, `c` is assigned the value `0`.
5. In the second const block, `d` is assigned the value `2 * 5`, `e` implicitly gets the same value as `d`, `f` is assigned `iota` (which starts at `0`), `g` gets the next value of `iota`, and `h` is assigned `10 * iota`.
6. The values of all constants are printed using `fmt.Println()`.


# Pointers

```go
package main

import "fmt"

func main() {
    // Define a string variable
    s := "Hello, world!"

    // Create a pointer to the string variable
    p := &s

    // Print the memory address stored in the pointer
    fmt.Println(p)

    // Dereference the pointer to access the value it points to
    fmt.Println(*p)

    // Modify the value indirectly through the pointer
    *p = "Hello, Gophers!"

    // Print the original string and the modified string
    fmt.Println(s, *p)

    // Create a new pointer to a string
    p = new(string)

    // Print the memory address stored in the new pointer and its value
    fmt.Println(p, *p)
}
```

### Output:
```
0xc000010200
Hello, world!
Hello, Gophers! Hello, Gophers!
0xc000010220 
```

### Explanation:

1. **Variable Declaration**: 
   - `s` is declared as a string variable with the value `"Hello, world!"`.

2. **Pointer Creation**:
   - `p` is declared as a pointer to a string (`*string`).
   - `&s` assigns the memory address of the variable `s` to the pointer `p`.

3. **Printing the Pointer**:
   - `fmt.Println(p)` prints the memory address stored in the pointer `p`.

4. **Dereferencing the Pointer**:
   - `fmt.Println(*p)` dereferences the pointer `p`, i.e., it accesses the value stored at the memory address pointed to by `p` and prints it.

5. **Modifying Value via Pointer**:
   - `*p = "Hello, Gophers!"` modifies the value indirectly through the pointer `p`. It changes the value of the variable `s` to `"Hello, Gophers!"`.

6. **Printing Original and Modified Values**:
   - `fmt.Println(s, *p)` prints both the original value of `s` and the modified value (pointed to by `p`).

7. **Creating a New Pointer**:
   - `p = new(string)` creates a new pointer to a string and assigns its memory address to `p`.

8. **Printing New Pointer**:
   - `fmt.Println(p, *p)` prints the memory address stored in the new pointer `p` (which is different from the previous pointer) and its zero-initialized value (empty string in this case).

This code demonstrates the basic concepts of pointers in Go, including creating pointers, accessing values through pointers, modifying values indirectly via pointers, and creating new pointers using the `new` function.


# Demo CLI Program For Text Input Uppercase Converter

This Go program prompts the user to input text, reads the input from the standard input (keyboard), converts it to uppercase, removes any leading or trailing whitespace, and then prints the modified text with an exclamation mark appended.

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

func main() {
	// Print prompt message
	fmt.Println("Insert Text")

	// Create a new buffered reader to read from standard input
	in := bufio.NewReader(os.Stdin)

	// Read a string from standard input until a newline character is encountered
	s, _ := in.ReadString('\n')

	// Remove leading and trailing whitespace from the input string
	s = strings.TrimSpace(s)

	// Convert the input string to uppercase
	s = strings.ToUpper(s)

	// Print the modified string with an exclamation mark appended
	fmt.Println(s + "!")
}
```

**Output:**
```
Insert Text
hi, my name is saklain
HI, MY NAME IS SAKLAIN!
```

**Explanation:**

1. **Prompt Message**: The program prints "Insert Text" to prompt the user to input text.

2. **Input Reading**: It creates a buffered reader `in` to read from the standard input (`os.Stdin`).

3. **Reading String**: The `ReadString('\n')` function reads a string from the standard input until it encounters a newline character ('\n'). The read string is stored in the variable `s`.

4. **Trimming Whitespace**: The `strings.TrimSpace()` function removes any leading or trailing whitespace from the input string `s`. This ensures that any extraneous whitespace entered by the user is removed.

5. **Uppercase Conversion**: The `strings.ToUpper()` function converts the input string `s` to uppercase. This ensures that the entire string is in uppercase characters.

6. **Printing Modified String**: Finally, the modified string `s` is printed to the standard output (`os.Stdout`) with an exclamation mark appended (`+ "!"`). This displays the converted uppercase string to the user.
## Working of the above CLI.
1. The program starts with a `package main` declaration, indicating that this is the main package that can be compiled into an executable program.

2. The required packages are imported:
   - `bufio`: This package implements buffered I/O and provides convenient functions for reading input.
   - `fmt`: This package implements formatted I/O and provides functions for printing and formatting input and output.
   - `os`: This package provides a platform-independent interface to operating system functionality, including access to standard input, standard output, and standard error.
   - `strings`: This package provides functions for manipulating strings.

3. The `main()` function is defined, which is the entry point of the program.

4. It prints "Insert Text" to the standard output.

5. It creates a new `bufio.Reader` called `in`, which reads from the standard input (`os.Stdin`).

6. It uses `in.ReadString('\n')` to read a string from the standard input until it encounters a newline (`'\n'`). It returns the string read and an error, but the error is ignored in this case (using `_`).

7. The read string `s` is then trimmed of any leading or trailing whitespace using `strings.TrimSpace(s)`.

8. The trimmed string is converted to uppercase using `strings.ToUpper(s)`.

9. Finally, the uppercase string is concatenated with an exclamation mark (`"!"`) and printed to the standard output using `fmt.Println()`.

So, when you run this program, it will print "Insert Text" and then wait for you to input a string. After you input a string and press Enter, it will convert that string to uppercase, trim any leading or trailing whitespace, append an exclamation mark to it, and then print the modified string with the exclamation mark.



# Demo Web Service Program for Serving Menu Text Using HTTP Server.

Code Explanation:
1. We begin by importing necessary packages:
   - `io`: Provides basic interfaces to I/O primitives.
   - `net/http`: Provides HTTP client and server implementations.
   - `os`: Provides operating system functionalities.

2. We define the `main()` function, which is the entry point of the program.
   - We register a handler function, `Handler`, to handle incoming HTTP requests at the root path ("/").
   - We start an HTTP server listening on port 3000 using `http.ListenAndServe()`.

3. We define the `Handler` function to handle HTTP requests.
   - Inside the handler function, we open the "menu.txt" file for reading.
   - We use `io.Copy()` to copy the contents of the file to the `http.ResponseWriter`, which sends the contents of the file back to the client who made the HTTP request.

4. The contents of the "menu.txt" file represent a menu with different items listed.

Program:
```go
package main

import (
	"io"
	"net/http"
	"os"
)

func main() {
	http.HandleFunc("/", Handler)
	http.ListenAndServe(":3000", nil)

}

func Handler(w http.ResponseWriter, r *http.Request) {
	f, _ := os.Open("menu.txt")

	io.Copy(w, f)
}
```

Text file (menu.txt):
```
Coffee
Espresso
Cappuccino

Hot Tea
Chai Tea
Chai Latte

Hot Chocolate
```

Output:
When you run this program and access http://localhost:3000 in your browser or send an HTTP request to this URL using a tool like cURL, it will display the contents of the "menu.txt" file, which is served by the Go HTTP server. The output will be the menu items listed in the text file, exactly as they appear in the file:

```
Coffee
Espresso
Cappuccino

Hot Tea
Chai Tea
Chai Latte

Hot Chocolate
```



# Basic Loops

```go
package main

import (
	"fmt"
)

func main() {
	// Part 1: Loop with a break
	i := 99
	for {
		fmt.Println(i)
		i += 1
		break
	}

	// Part 2: Loop with a condition
	i = 5
	for i < 10 {
		fmt.Println(i)
		i++
	}

	// Part 3: Loop with initialization, condition, and post statement
	for i := 0; i < 10; i++ {
		fmt.Println(i)
	}
}
```

Explanation:
1. **Part 1**: In this section, a `for` loop is used without any condition. It continues indefinitely until a `break` statement is encountered. Inside the loop, the variable `i` is printed, incremented by 1, and then the loop is exited with `break`.

2. **Part 2**: This section demonstrates a `for` loop with a condition (`i < 10`). The loop continues executing as long as the condition (`i < 10`) is true. Inside the loop, the value of `i` is printed, incremented by 1, and the loop continues until `i` becomes equal to or greater than 10.

3. **Part 3**: Here, a typical `for` loop construct with initialization (`i := 0`), condition (`i < 10`), and post statement (`i++`) is used. The loop initializes `i` to 0, continues as long as `i` is less than 10, increments `i` by 1 in each iteration, and prints the value of `i`.

Output:
```
99
5
6
7
8
9
0
1
2
3
4
5
6
7
8
9
```

In the output, you can see:
- The initial value of `i` is printed in the first loop (`99`).
- In the second loop, the values of `i` from `5` to `9` are printed.
- In the third loop, the values of `i` from `0` to `9` are printed again.



# Looping Over Collection
## Before


Program:
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

func main() {
	fmt.Println("Please select an option")
	fmt.Println("1) Print menu")
	in := bufio.NewReader(os.Stdin)
	choice, _ := in.ReadString('\n')
	choice = strings.TrimSpace(choice) // we don't know what to do with this yet!

	type menuItem struct {
		name   string
		prices map[string]float64
	}

	menu := []menuItem{
		{name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
		{name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
	}

	fmt.Println(menu)
}
```


Output:
```
Please select an option
1) Print menu
[{Coffee map[small:1.65 medium:1.8 large:1.95]} {Espresso map[single:1.9 double:2.25 triple:2.55]}]
```

Explanation:
- This Go program displays a simple menu and allows the user to select an option.
- It first prints a prompt asking the user to select an option.
- Then, it reads the user's input using `bufio.NewReader(os.Stdin)`.
- The user's input is stored in the variable `choice`.
- The `strings.TrimSpace()` function is used to remove any leading or trailing whitespace from the user's input. Currently, there is no action based on the user's choice, so this line is a placeholder.
- Next, a custom type `menuItem` is defined, representing an item in the menu. It contains the name of the item and a map of prices for different sizes or options.
- The menu is defined as a slice of `menuItem` structs, with each item having a name and a map of prices.
- Finally, the program prints the menu using `fmt.Println(menu)`.

The output displays the menu items along with their respective prices in a structured format.

## After

This Go program presents an interactive menu where the user can select an option. If the user chooses to print the menu, it displays a list of items along with their sizes and prices.

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

func main() {
	// Prompt the user to select an option
	fmt.Println("Please select an option")
	fmt.Println("1) Print menu")

	// Read the user's choice from standard input
	in := bufio.NewReader(os.Stdin)
	choice, _ := in.ReadString('\n')

	// Remove leading/trailing whitespace from the choice
	choice = strings.TrimSpace(choice) // we don't know what to do with this yet!

	// Define a struct to represent menu items
	type menuItem struct {
		name   string            // Name of the item
		prices map[string]float64 // Prices for different sizes
	}

	// Define the menu items
	menu := []menuItem{
		{name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
		{name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
	}

	// Print the menu
	for _, item := range menu {
		fmt.Println(item.name)
		fmt.Println(strings.Repeat("-", 10))
		for size, cost := range item.prices {
			fmt.Printf("\t%10s%10.2f\n", size, cost)
		}
	}
}
```

**Output:**
```
Please select an option
1) Print menu
Coffee
----------
	    small      1.65
	   medium      1.80
	    large      1.95
Espresso
----------
	   single      1.90
	   double      2.25
	  triple      2.55
```

**Explanation:**
- The program starts by prompting the user to select an option and prints the option to print the menu.
- It reads the user's choice from the standard input.
- The `strings.TrimSpace()` function is used to remove any leading or trailing whitespace from the user's choice. Currently, there's no functionality implemented based on the user's choice, so it's not utilized further.
- The program defines a struct named `menuItem`, which represents a menu item. It has two fields: `name` for the name of the item and `prices` for a map of prices for different sizes.
- The program then defines a slice named `menu` containing various `menuItem` structs representing different items on the menu along with their prices for different sizes.
- It iterates over each item in the `menu` slice and prints the name of the item followed by a series of dashes.
- For each item, it iterates over the prices map and prints each size along with its corresponding price.


Looping over a collection before and after each change can have significant differences in terms of the behavior and outcomes of the loop.

1. **Looping Over Collection Before Making Changes:**
   - When you loop over a collection before making changes, you're essentially iterating over the original state of the collection.
   - Any modifications made to the collection during the loop iteration won't affect the current iteration. This means that you're not modifying the collection you're iterating over, but rather perhaps creating a new collection based on the original one.
   - This approach is often used when you want to analyze or process the existing data without altering it directly.

2. **Looping Over Collection After Making Changes:**
   - When you loop over a collection after making changes, you're working with the modified state of the collection.
   - Any modifications made to the collection during the loop iteration will impact the current iteration, potentially altering the behavior of the loop.
   - This approach is often used when you need to perform operations that involve modifying the collection itself, such as removing elements that meet certain conditions or updating values based on specific criteria.

In simple terms, looping over a collection before making changes allows you to inspect the original data without affecting it, while looping over a collection after making changes enables you to apply modifications directly to the collection as you iterate over it.

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

func main() {
	fmt.Println("Insert Text")
	in := bufio.NewReader(os.Stdin)
	s, _ := in.ReadString('\n')
	s = strings.TrimSpace(s)
	s = strings.ToUpper(s)
	fmt.Println(s + "!")
}
```

```go
Insert Text
hi, my name is saklain
HI, MY NAME IS SAKLAIN!
```

This Go code reads a string from the standard input (keyboard input), converts it to uppercase, trims any leading or trailing whitespace, and then prints it with an exclamation mark.

Here's a step-by-step explanation of the code:

# Arrays 
```go
package main

import "fmt"

func main() {
    // Declaring an array of strings with length 3
    var arr [3]string
    fmt.Println(arr) // Output: [  ]

    // Initializing the array with values
    arr = [3]string{"Coffee", "Espresso", "Cappuccino"}
    fmt.Println(arr) // Output: [Coffee Espresso Cappuccino]

    // Accessing an element of the array
    fmt.Println(arr[1]) // Output: Espresso

    // Modifying an element of the array
    arr[1] = "Chai Tea"
    fmt.Println(arr) // Output: [Coffee Chai Tea Cappuccino]

    // Creating a new array and copying values from the original array
    arr2 := arr
    arr2[2] = "Chai Latte"
    
    // Printing both arrays
    fmt.Println(arr, arr2) // Output: [Coffee Chai Tea Cappuccino] [Coffee Chai Tea Chai Latte]
}
```

**Output:**
```
[  ]
[Coffee Espresso Cappuccino]
Espresso
[Coffee Chai Tea Cappuccino]
[Coffee Chai Tea Cappuccino] [Coffee Chai Tea Chai Latte]
```

**Explanation:**

1. **Array Declaration and Initialization:**
   - An array `arr` of type string with a length of 3 is declared.
   - Initially, since no values are assigned, the elements are initialized with their zero values, which for strings is an empty string.
   - The array is printed, resulting in `[]`.

2. **Array Initialization with Values:**
   - The array `arr` is initialized with specific string values: "Coffee", "Espresso", and "Cappuccino".
   - The array is printed, resulting in `[Coffee Espresso Cappuccino]`.

3. **Accessing Elements:**
   - The second element of the array (index 1), "Espresso", is accessed and printed.

4. **Modifying Elements:**
   - The second element of the array is modified from "Espresso" to "Chai Tea".
   - The modified array is printed, resulting in `[Coffee Chai Tea Cappuccino]`.

5. **Copying Arrays:**
   - A new array `arr2` is created, and the values of `arr` are copied into it.
   - The third element of `arr2` is modified from "Cappuccino" to "Chai Latte".
   - Both `arr` and `arr2` are printed, showing the modification only in `arr2`.

# Slices 

```go
package main

import (
	"fmt"
	"slices"
)

func main() {
	var s []string
	fmt.Println(s) // Output: []

	s = []string{"Coffee", "Espresso", "Cappuccino"}
	fmt.Println(s) // Output: [Coffee Espresso Cappuccino]

	fmt.Println(s[1]) // Output: Espresso
	s[1] = "Chai Tea"
	fmt.Println(s) // Output: [Coffee Chai Tea Cappuccino]

	s = append(s, "Hot Chocolate", "Hot Tea")
	fmt.Println(s) // Output: [Coffee Chai Tea Cappuccino Hot Chocolate Hot Tea]

	s = slices.Delete(s, 1, 2)
	fmt.Println(s) // Output: [Coffee Cappuccino Hot Chocolate Hot Tea]

	s2 := s

	s[2] = "Chai Latte"

	fmt.Println(s, s2) // Output: [Coffee Cappuccino Chai Latte Hot Chocolate Hot Tea] [Coffee Cappuccino Chai Latte Hot Chocolate Hot Tea]
}
```

Explanation:

1. The program imports a custom package named "slices" that contains a function named `Delete`.

2. In the `main` function:
   - An empty slice of strings `s` is declared and printed (`[]`).
   - The slice `s` is initialized with three string elements: "Coffee", "Espresso", and "Cappuccino", and then printed.
   - The second element of slice `s` (index 1) is printed, which is "Espresso". Then, it is replaced with "Chai Tea", and the modified slice is printed.
   - Two more string elements, "Hot Chocolate" and "Hot Tea", are appended to the slice `s`, and the modified slice is printed.
   - The `Delete` function from the "slices" package is called to delete elements at indices 1 and 2 from slice `s`, and the modified slice is printed.
   - A new slice `s2` is declared and assigned the value of slice `s`.
   - The third element of slice `s` (index 2) is modified to "Chai Latte".
   - Both slices `s` and `s2` are printed to observe the change. Both slices reflect the modification made to slice `s`.

Output:
```
[]
[Coffee Espresso Cappuccino]
Espresso
[Coffee Chai Tea Cappuccino]
[Coffee Chai Tea Cappuccino Hot Chocolate Hot Tea]
[Coffee Cappuccino Hot Chocolate Hot Tea]
[Coffee Cappuccino Chai Latte Hot Chocolate Hot Tea] [Coffee Cappuccino Chai Latte Hot Chocolate Hot Tea]
```

This code shows different things you can do with slices in Go. Slices are like lists in other programming languages. You can do things like create them, change what's inside them, add new stuff to them, take things out of them, and copy them.
- It starts by creating a slice, which is like a list, and prints it out.
- Then, it changes something inside the slice and prints it again.
- After that, it adds something new to the slice and prints it again.
- Next, it removes something from the slice and prints it again.
- Finally, it copies the slice and prints both the original and the copy to show they are separate but have the same content.

# Maps

```go
package main

import (
	"fmt"
)

func main() {
	// Declare a map variable m with keys of type string and values of type slice of string
	var m map[string][]string
	fmt.Println("Initial map:", m) // Output: Initial map: map[]

	// Initialize map m with key-value pairs
	m = map[string][]string{
		"coffee": {"Coffee", "Espresso", "Cappuccino"},
		"tea":    {"Hot Tea", "Chai Tea", "Chai Latte"},
	}

	fmt.Println("Map after initialization:", m) // Output: Map after initialization: map[coffee:[Coffee Espresso Cappuccino] tea:[Hot Tea Chai Tea Chai Latte]]

	// Access and print the value associated with the key "coffee"
	fmt.Println("Values for 'coffee':", m["coffee"]) // Output: Values for 'coffee': [Coffee Espresso Cappuccino]

	// Delete the key-value pair with key "tea"
	delete(m, "tea")
	fmt.Println("Map after deletion:", m) // Output: Map after deletion: map[coffee:[Coffee Espresso Cappuccino]]

	// Add a new key-value pair to the map
	m["other"] = []string{"Hot Chocolate"}
	fmt.Println("Map after addition:", m) // Output: Map after addition: map[coffee:[Coffee Espresso Cappuccino] other:[Hot Chocolate]]

	// Accessing a non-existent key "tea"
	fmt.Println("Values for 'tea':", m["tea"]) // Output: Values for 'tea': []

	// Check if a key "tea" exists in the map
	v, ok := m["tea"]
	fmt.Println("Value for 'tea':", v, "Existence:", ok) // Output: Value for 'tea': [] Existence: false

	// Assigning map m to another map variable m2
	m2 := m
	// Modify the value associated with the key "coffee" in map m2
	m2["coffee"] = []string{"Coffee"}
	// Modify the value associated with the key "tea" in map m
	m["tea"] = []string{"Hot Tea"}

	fmt.Println("Map m after modification:", m)   // Output: Map m after modification: map[coffee:[Coffee] other:[Hot Chocolate] tea:[Hot Tea]]
	fmt.Println("Map m2 after modification:", m2) // Output: Map m2 after modification: map[coffee:[Coffee] other:[Hot Chocolate] tea:[Hot Tea]]
}
```

**Output:**

```
Initial map: map[]
Map after initialization: map[coffee:[Coffee Espresso Cappuccino] tea:[Hot Tea Chai Tea Chai Latte]]
Values for 'coffee': [Coffee Espresso Cappuccino]
Map after deletion: map[coffee:[Coffee Espresso Cappuccino]]
Map after addition: map[coffee:[Coffee Espresso Cappuccino] other:[Hot Chocolate]]
Values for 'tea': []
Value for 'tea': [] Existence: false
Map m after modification: map[coffee:[Coffee] other:[Hot Chocolate] tea:[Hot Tea]]
Map m2 after modification: map[coffee:[Coffee] other:[Hot Chocolate] tea:[Hot Tea]]
```

**Explanation:**
This program is about using maps in Go. A map is like a dictionary where each item has a key and a value. 

- At the beginning, a map called `m` is made, but it's empty. We print it out, so it shows nothing.
- Then, we add some key-value pairs to the map. The keys are words, and the values are lists of words.
- Next, we do different things with the map like getting items by their key, removing items, adding new items, and checking if a key exists.
- Finally, we show that if you copy a map into another one, they both point to the same information. So if you change something in one map, it changes in the other map too.

# Struct


```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

func main() {
	// Print initial message
	fmt.Println("Please select an option")
	fmt.Println("1) Print menu")

	// Read user input
	in := bufio.NewReader(os.Stdin)
	choice, _ := in.ReadString('\n')
	choice = strings.TrimSpace(choice) // We don't know what to do with this yet!

	// Define a struct for menu items
	type menuItem struct {
		name   string
		prices map[string]float64
	}

	// Define menu items with their respective prices
	menu := []menuItem{
		{name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
		{name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
	}

	// Print the menu
	fmt.Println(menu)
}
```


**Output**:

```
Please select an option
1) Print menu
[{Coffee map[large:1.95 medium:1.8 small:1.65]} {Espresso map[double:2.25 single:1.9 triple:2.55]}]
```


**Explanation**:

- The program starts by printing a message prompting the user to select an option and printing the option to print the menu.

- It then reads the user's input using `bufio.NewReader(os.Stdin)` to create a reader to read from standard input, and `ReadString('\n')` to read until the user presses Enter. The input is stored in the variable `choice`.

- `strings.TrimSpace(choice)` is used to remove any leading or trailing whitespace from the user's input. However, at this stage of the code, we haven't implemented what to do with the user's choice yet.

- A custom type `menuItem` is defined, which represents a menu item. It has two fields: `name` (string) representing the name of the item and `prices` (map[string]float64) representing the prices of the item for different sizes or options.

- An array `menu` of `menuItem` structs is defined, containing two menu items: "Coffee" and "Espresso", each with their respective prices for different options.

- Finally, the program prints the entire menu array.



# Variables

```go
package main

import "fmt"

func main() {
    // Declare a variable 'a' of type string and assign the value "foo" to it
    var a string
    a = "foo"

    // Print the value of variable 'a'
    fmt.Println(a)

    // Declare a variable 'b' of type int and assign the value 99 to it
    var b int = 99
    // Print the value of variable 'b'
    fmt.Println(b)

    // Declare a variable 'c' and let Go infer its type as bool, and assign the value true to it
    var c = true
    // Print the value of variable 'c'
    fmt.Println(c)

    // Declare a variable 'd' and let Go infer its type as float64, and assign the value 3.1415 to it
    d := 3.1415
    // Print the value of variable 'd'
    fmt.Println(d)

    // Convert the value of 'd' to an integer and assign it to variable 'e'
    var e int = int(d)
    // Print the value of variable 'e'
    fmt.Println(e)
}
```

**Output:**
```
foo
99
true
3.1415
3
```

**Explanation:**

1. In this Go program, we declare and initialize variables of different types and print their values.

2. `var a string` declares a variable `a` of type string. We assign the value "foo" to `a` using `a = "foo"`.

3. `fmt.Println(a)` prints the value of `a`, which is "foo".

4. `var b int = 99` declares a variable `b` of type int and assigns it the value 99.

5. `fmt.Println(b)` prints the value of `b`, which is 99.

6. `var c = true` declares a variable `c` without explicitly specifying its type. Go infers the type of `c` as bool based on the assigned value true.

7. `fmt.Println(c)` prints the value of `c`, which is true.

8. `d := 3.1415` declares a variable `d` and lets Go infer its type as float64. We assign the value 3.1415 to `d`.

9. `fmt.Println(d)` prints the value of `d`, which is 3.1415.

10. `var e int = int(d)` converts the value of `d` to an integer and assigns it to variable `e`.

11. `fmt.Println(e)` prints the value of `e`, which is the truncated integer part of the value stored in `d`, in this case, 3.







# Arithmetic Operations

This Go program demonstrates basic arithmetic operations such as addition, subtraction, multiplication, division, and modulus. It also showcases type conversion and comparison operators.

```go
package main

import "fmt"

func main() {
    // Declaring two integer variables
    a, b := 5, 2

    // Addition
    fmt.Println(a + b)

    // Subtraction
    fmt.Println(a - b)

    // Multiplication
    fmt.Println(a * b)

    // Integer division (result is an integer)
    fmt.Println(a / b)

    // Modulus (remainder of integer division)
    fmt.Println(a % b)

    // Float division (result is a floating-point number)
    fmt.Println(float32(a) / float32(b))

    // Comparison operators
    fmt.Println(a == b) // Equal to
    fmt.Println(a < b)  // Less than
    fmt.Println(a > b)  // Greater than
}
```

Output:
```
7
3
10
2
1
2.5
false
false
true
```

Explanation:
- The program begins by declaring two integer variables `a` and `b` with values 5 and 2, respectively.
- It then performs various arithmetic operations:
  - Addition (`a + b`): 5 + 2 = 7
  - Subtraction (`a - b`): 5 - 2 = 3
  - Multiplication (`a * b`): 5 * 2 = 10
  - Integer division (`a / b`): 5 / 2 = 2 (integer division truncates the decimal part)
  - Modulus (`a % b`): 5 % 2 = 1 (remainder of 5 divided by 2)
  - Float division (`float32(a) / float32(b)`): 5.0 / 2.0 = 2.5 (explicit type conversion to float32)
- Finally, it demonstrates comparison operators:
  - Equal to (`a == b`): 5 is not equal to 2, so it prints `false`
  - Less than (`a < b`): 5 is not less than 2, so it prints `false`
  - Greater than (`a > b`): 5 is greater than 2, so it prints `true`

 
# Constants
This Go program demonstrates the usage of constants and the `iota` identifier.

```go
package main

import "fmt"

func main() {
    // Constants with explicit types
    const a = 42
    const b float32 = 3

    // Assigning constants to variables with compatible types
    var i int = a
    fmt.Println(i)
    var f32 float32 = a
    fmt.Println(f32)

    // Assigning constant 'b' to variable 'f32'
    f32 = b
    fmt.Println(f32)

    // iota usage in constant declarations
    const c = iota
    fmt.Println(c)

    // Using iota in a const block
    const (
        d = 2 * 5
        e     // e = 2 * 5 (implicitly)
        f = iota  // f = 0
        g         // g = 1 (incremented from iota)
        h = 10 * iota  // h = 10 * 2
    )

    // Printing values of constants
    fmt.Println(d, e, f, g, h)
}
```

### Output

```
42
42
3
0
10 10 0 1 20
```

### Explanation

1. Constants `a` and `b` are declared with values `42` and `3` respectively. `a` is untyped, and `b` is explicitly typed as `float32`.
2. Constant `a` is assigned to variable `i` of type `int`, and `f32` of type `float32`. Go allows this because the values are compatible.
3. Constant `b` is assigned to variable `f32`.
4. The `iota` identifier is used to generate sequential integer values in a const block. In this case, `c` is assigned the value `0`.
5. In the second const block, `d` is assigned the value `2 * 5`, `e` implicitly gets the same value as `d`, `f` is assigned `iota` (which starts at `0`), `g` gets the next value of `iota`, and `h` is assigned `10 * iota`.
6. The values of all constants are printed using `fmt.Println()`.


# Pointers

```go
package main

import "fmt"

func main() {
    // Define a string variable
    s := "Hello, world!"

    // Create a pointer to the string variable
    p := &s

    // Print the memory address stored in the pointer
    fmt.Println(p)

    // Dereference the pointer to access the value it points to
    fmt.Println(*p)

    // Modify the value indirectly through the pointer
    *p = "Hello, Gophers!"

    // Print the original string and the modified string
    fmt.Println(s, *p)

    // Create a new pointer to a string
    p = new(string)

    // Print the memory address stored in the new pointer and its value
    fmt.Println(p, *p)
}
```

### Output:
```
0xc000010200
Hello, world!
Hello, Gophers! Hello, Gophers!
0xc000010220 
```

### Explanation:

1. **Variable Declaration**: 
   - `s` is declared as a string variable with the value `"Hello, world!"`.

2. **Pointer Creation**:
   - `p` is declared as a pointer to a string (`*string`).
   - `&s` assigns the memory address of the variable `s` to the pointer `p`.

3. **Printing the Pointer**:
   - `fmt.Println(p)` prints the memory address stored in the pointer `p`.

4. **Dereferencing the Pointer**:
   - `fmt.Println(*p)` dereferences the pointer `p`, i.e., it accesses the value stored at the memory address pointed to by `p` and prints it.

5. **Modifying Value via Pointer**:
   - `*p = "Hello, Gophers!"` modifies the value indirectly through the pointer `p`. It changes the value of the variable `s` to `"Hello, Gophers!"`.

6. **Printing Original and Modified Values**:
   - `fmt.Println(s, *p)` prints both the original value of `s` and the modified value (pointed to by `p`).

7. **Creating a New Pointer**:
   - `p = new(string)` creates a new pointer to a string and assigns its memory address to `p`.

8. **Printing New Pointer**:
   - `fmt.Println(p, *p)` prints the memory address stored in the new pointer `p` (which is different from the previous pointer) and its zero-initialized value (empty string in this case).

This code demonstrates the basic concepts of pointers in Go, including creating pointers, accessing values through pointers, modifying values indirectly via pointers, and creating new pointers using the `new` function.


# Demo CLI Program For Text Input Uppercase Converter

This Go program prompts the user to input text, reads the input from the standard input (keyboard), converts it to uppercase, removes any leading or trailing whitespace, and then prints the modified text with an exclamation mark appended.

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

func main() {
	// Print prompt message
	fmt.Println("Insert Text")

	// Create a new buffered reader to read from standard input
	in := bufio.NewReader(os.Stdin)

	// Read a string from standard input until a newline character is encountered
	s, _ := in.ReadString('\n')

	// Remove leading and trailing whitespace from the input string
	s = strings.TrimSpace(s)

	// Convert the input string to uppercase
	s = strings.ToUpper(s)

	// Print the modified string with an exclamation mark appended
	fmt.Println(s + "!")
}
```

**Output:**
```
Insert Text
hi, my name is saklain
HI, MY NAME IS SAKLAIN!
```

**Explanation:**

1. **Prompt Message**: The program prints "Insert Text" to prompt the user to input text.

2. **Input Reading**: It creates a buffered reader `in` to read from the standard input (`os.Stdin`).

3. **Reading String**: The `ReadString('\n')` function reads a string from the standard input until it encounters a newline character ('\n'). The read string is stored in the variable `s`.

4. **Trimming Whitespace**: The `strings.TrimSpace()` function removes any leading or trailing whitespace from the input string `s`. This ensures that any extraneous whitespace entered by the user is removed.

5. **Uppercase Conversion**: The `strings.ToUpper()` function converts the input string `s` to uppercase. This ensures that the entire string is in uppercase characters.

6. **Printing Modified String**: Finally, the modified string `s` is printed to the standard output (`os.Stdout`) with an exclamation mark appended (`+ "!"`). This displays the converted uppercase string to the user.
## Working of the above CLI.
1. The program starts with a `package main` declaration, indicating that this is the main package that can be compiled into an executable program.

2. The required packages are imported:
   - `bufio`: This package implements buffered I/O and provides convenient functions for reading input.
   - `fmt`: This package implements formatted I/O and provides functions for printing and formatting input and output.
   - `os`: This package provides a platform-independent interface to operating system functionality, including access to standard input, standard output, and standard error.
   - `strings`: This package provides functions for manipulating strings.

3. The `main()` function is defined, which is the entry point of the program.

4. It prints "Insert Text" to the standard output.

5. It creates a new `bufio.Reader` called `in`, which reads from the standard input (`os.Stdin`).

6. It uses `in.ReadString('\n')` to read a string from the standard input until it encounters a newline (`'\n'`). It returns the string read and an error, but the error is ignored in this case (using `_`).

7. The read string `s` is then trimmed of any leading or trailing whitespace using `strings.TrimSpace(s)`.

8. The trimmed string is converted to uppercase using `strings.ToUpper(s)`.

9. Finally, the uppercase string is concatenated with an exclamation mark (`"!"`) and printed to the standard output using `fmt.Println()`.

So, when you run this program, it will print "Insert Text" and then wait for you to input a string. After you input a string and press Enter, it will convert that string to uppercase, trim any leading or trailing whitespace, append an exclamation mark to it, and then print the modified string with the exclamation mark.



# Demo Web Service Program for Serving Menu Text Using HTTP Server.

Code Explanation:
1. We begin by importing necessary packages:
   - `io`: Provides basic interfaces to I/O primitives.
   - `net/http`: Provides HTTP client and server implementations.
   - `os`: Provides operating system functionalities.

2. We define the `main()` function, which is the entry point of the program.
   - We register a handler function, `Handler`, to handle incoming HTTP requests at the root path ("/").
   - We start an HTTP server listening on port 3000 using `http.ListenAndServe()`.

3. We define the `Handler` function to handle HTTP requests.
   - Inside the handler function, we open the "menu.txt" file for reading.
   - We use `io.Copy()` to copy the contents of the file to the `http.ResponseWriter`, which sends the contents of the file back to the client who made the HTTP request.

4. The contents of the "menu.txt" file represent a menu with different items listed.

Program:
```go
package main

import (
	"io"
	"net/http"
	"os"
)

func main() {
	http.HandleFunc("/", Handler)
	http.ListenAndServe(":3000", nil)

}

func Handler(w http.ResponseWriter, r *http.Request) {
	f, _ := os.Open("menu.txt")

	io.Copy(w, f)
}
```

Text file (menu.txt):
```
Coffee
Espresso
Cappuccino

Hot Tea
Chai Tea
Chai Latte

Hot Chocolate
```

Output:
When you run this program and access http://localhost:3000 in your browser or send an HTTP request to this URL using a tool like cURL, it will display the contents of the "menu.txt" file, which is served by the Go HTTP server. The output will be the menu items listed in the text file, exactly as they appear in the file:

```
Coffee
Espresso
Cappuccino

Hot Tea
Chai Tea
Chai Latte

Hot Chocolate
```



# Basic Loops

```go
package main

import (
	"fmt"
)

func main() {
	// Part 1: Loop with a break
	i := 99
	for {
		fmt.Println(i)
		i += 1
		break
	}

	// Part 2: Loop with a condition
	i = 5
	for i < 10 {
		fmt.Println(i)
		i++
	}

	// Part 3: Loop with initialization, condition, and post statement
	for i := 0; i < 10; i++ {
		fmt.Println(i)
	}
}
```

Explanation:
1. **Part 1**: In this section, a `for` loop is used without any condition. It continues indefinitely until a `break` statement is encountered. Inside the loop, the variable `i` is printed, incremented by 1, and then the loop is exited with `break`.

2. **Part 2**: This section demonstrates a `for` loop with a condition (`i < 10`). The loop continues executing as long as the condition (`i < 10`) is true. Inside the loop, the value of `i` is printed, incremented by 1, and the loop continues until `i` becomes equal to or greater than 10.

3. **Part 3**: Here, a typical `for` loop construct with initialization (`i := 0`), condition (`i < 10`), and post statement (`i++`) is used. The loop initializes `i` to 0, continues as long as `i` is less than 10, increments `i` by 1 in each iteration, and prints the value of `i`.

Output:
```
99
5
6
7
8
9
0
1
2
3
4
5
6
7
8
9
```

In the output, you can see:
- The initial value of `i` is printed in the first loop (`99`).
- In the second loop, the values of `i` from `5` to `9` are printed.
- In the third loop, the values of `i` from `0` to `9` are printed again.



# Looping Over Collection
## Before


Program:
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

func main() {
	fmt.Println("Please select an option")
	fmt.Println("1) Print menu")
	in := bufio.NewReader(os.Stdin)
	choice, _ := in.ReadString('\n')
	choice = strings.TrimSpace(choice) // we don't know what to do with this yet!

	type menuItem struct {
		name   string
		prices map[string]float64
	}

	menu := []menuItem{
		{name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
		{name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
	}

	fmt.Println(menu)
}
```


Output:
```
Please select an option
1) Print menu
[{Coffee map[small:1.65 medium:1.8 large:1.95]} {Espresso map[single:1.9 double:2.25 triple:2.55]}]
```

Explanation:
- This Go program displays a simple menu and allows the user to select an option.
- It first prints a prompt asking the user to select an option.
- Then, it reads the user's input using `bufio.NewReader(os.Stdin)`.
- The user's input is stored in the variable `choice`.
- The `strings.TrimSpace()` function is used to remove any leading or trailing whitespace from the user's input. Currently, there is no action based on the user's choice, so this line is a placeholder.
- Next, a custom type `menuItem` is defined, representing an item in the menu. It contains the name of the item and a map of prices for different sizes or options.
- The menu is defined as a slice of `menuItem` structs, with each item having a name and a map of prices.
- Finally, the program prints the menu using `fmt.Println(menu)`.

The output displays the menu items along with their respective prices in a structured format.

## After

This Go program presents an interactive menu where the user can select an option. If the user chooses to print the menu, it displays a list of items along with their sizes and prices.

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

func main() {
	// Prompt the user to select an option
	fmt.Println("Please select an option")
	fmt.Println("1) Print menu")

	// Read the user's choice from standard input
	in := bufio.NewReader(os.Stdin)
	choice, _ := in.ReadString('\n')

	// Remove leading/trailing whitespace from the choice
	choice = strings.TrimSpace(choice) // we don't know what to do with this yet!

	// Define a struct to represent menu items
	type menuItem struct {
		name   string            // Name of the item
		prices map[string]float64 // Prices for different sizes
	}

	// Define the menu items
	menu := []menuItem{
		{name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
		{name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
	}

	// Print the menu
	for _, item := range menu {
		fmt.Println(item.name)
		fmt.Println(strings.Repeat("-", 10))
		for size, cost := range item.prices {
			fmt.Printf("\t%10s%10.2f\n", size, cost)
		}
	}
}
```

**Output:**
```
Please select an option
1) Print menu
Coffee
----------
	    small      1.65
	   medium      1.80
	    large      1.95
Espresso
----------
	   single      1.90
	   double      2.25
	  triple      2.55
```

**Explanation:**
- The program starts by prompting the user to select an option and prints the option to print the menu.
- It reads the user's choice from the standard input.
- The `strings.TrimSpace()` function is used to remove any leading or trailing whitespace from the user's choice. Currently, there's no functionality implemented based on the user's choice, so it's not utilized further.
- The program defines a struct named `menuItem`, which represents a menu item. It has two fields: `name` for the name of the item and `prices` for a map of prices for different sizes.
- The program then defines a slice named `menu` containing various `menuItem` structs representing different items on the menu along with their prices for different sizes.
- It iterates over each item in the `menu` slice and prints the name of the item followed by a series of dashes.
- For each item, it iterates over the prices map and prints each size along with its corresponding price.


Looping over a collection before and after each change can have significant differences in terms of the behavior and outcomes of the loop.

1. **Looping Over Collection Before Making Changes:**
   - When you loop over a collection before making changes, you're essentially iterating over the original state of the collection.
   - Any modifications made to the collection during the loop iteration won't affect the current iteration. This means that you're not modifying the collection you're iterating over, but rather perhaps creating a new collection based on the original one.
   - This approach is often used when you want to analyze or process the existing data without altering it directly.

2. **Looping Over Collection After Making Changes:**
   - When you loop over a collection after making changes, you're working with the modified state of the collection.
   - Any modifications made to the collection during the loop iteration will impact the current iteration, potentially altering the behavior of the loop.
   - This approach is often used when you need to perform operations that involve modifying the collection itself, such as removing elements that meet certain conditions or updating values based on specific criteria.

In simple terms, looping over a collection before making changes allows you to inspect the original data without affecting it, while looping over a collection after making changes enables you to apply modifications directly to the collection as you iterate over it.

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

func main() {
	fmt.Println("Insert Text")
	in := bufio.NewReader(os.Stdin)
	s, _ := in.ReadString('\n')
	s = strings.TrimSpace(s)
	s = strings.ToUpper(s)
	fmt.Println(s + "!")
}
```

```go
Insert Text
hi, my name is saklain
HI, MY NAME IS SAKLAIN!
```

This Go code reads a string from the standard input (keyboard input), converts it to uppercase, trims any leading or trailing whitespace, and then prints it with an exclamation mark.

Here's a step-by-step explanation of the code:

# Arrays 
```go
package main

import "fmt"

func main() {
    // Declaring an array of strings with length 3
    var arr [3]string
    fmt.Println(arr) // Output: [  ]

    // Initializing the array with values
    arr = [3]string{"Coffee", "Espresso", "Cappuccino"}
    fmt.Println(arr) // Output: [Coffee Espresso Cappuccino]

    // Accessing an element of the array
    fmt.Println(arr[1]) // Output: Espresso

    // Modifying an element of the array
    arr[1] = "Chai Tea"
    fmt.Println(arr) // Output: [Coffee Chai Tea Cappuccino]

    // Creating a new array and copying values from the original array
    arr2 := arr
    arr2[2] = "Chai Latte"
    
    // Printing both arrays
    fmt.Println(arr, arr2) // Output: [Coffee Chai Tea Cappuccino] [Coffee Chai Tea Chai Latte]
}
```

**Output:**
```
[  ]
[Coffee Espresso Cappuccino]
Espresso
[Coffee Chai Tea Cappuccino]
[Coffee Chai Tea Cappuccino] [Coffee Chai Tea Chai Latte]
```

**Explanation:**

1. **Array Declaration and Initialization:**
   - An array `arr` of type string with a length of 3 is declared.
   - Initially, since no values are assigned, the elements are initialized with their zero values, which for strings is an empty string.
   - The array is printed, resulting in `[]`.

2. **Array Initialization with Values:**
   - The array `arr` is initialized with specific string values: "Coffee", "Espresso", and "Cappuccino".
   - The array is printed, resulting in `[Coffee Espresso Cappuccino]`.

3. **Accessing Elements:**
   - The second element of the array (index 1), "Espresso", is accessed and printed.

4. **Modifying Elements:**
   - The second element of the array is modified from "Espresso" to "Chai Tea".
   - The modified array is printed, resulting in `[Coffee Chai Tea Cappuccino]`.

5. **Copying Arrays:**
   - A new array `arr2` is created, and the values of `arr` are copied into it.
   - The third element of `arr2` is modified from "Cappuccino" to "Chai Latte".
   - Both `arr` and `arr2` are printed, showing the modification only in `arr2`.

# Slices 

```go
package main

import (
	"fmt"
	"slices"
)

func main() {
	var s []string
	fmt.Println(s) // Output: []

	s = []string{"Coffee", "Espresso", "Cappuccino"}
	fmt.Println(s) // Output: [Coffee Espresso Cappuccino]

	fmt.Println(s[1]) // Output: Espresso
	s[1] = "Chai Tea"
	fmt.Println(s) // Output: [Coffee Chai Tea Cappuccino]

	s = append(s, "Hot Chocolate", "Hot Tea")
	fmt.Println(s) // Output: [Coffee Chai Tea Cappuccino Hot Chocolate Hot Tea]

	s = slices.Delete(s, 1, 2)
	fmt.Println(s) // Output: [Coffee Cappuccino Hot Chocolate Hot Tea]

	s2 := s

	s[2] = "Chai Latte"

	fmt.Println(s, s2) // Output: [Coffee Cappuccino Chai Latte Hot Chocolate Hot Tea] [Coffee Cappuccino Chai Latte Hot Chocolate Hot Tea]
}
```

Explanation:

1. The program imports a custom package named "slices" that contains a function named `Delete`.

2. In the `main` function:
   - An empty slice of strings `s` is declared and printed (`[]`).
   - The slice `s` is initialized with three string elements: "Coffee", "Espresso", and "Cappuccino", and then printed.
   - The second element of slice `s` (index 1) is printed, which is "Espresso". Then, it is replaced with "Chai Tea", and the modified slice is printed.
   - Two more string elements, "Hot Chocolate" and "Hot Tea", are appended to the slice `s`, and the modified slice is printed.
   - The `Delete` function from the "slices" package is called to delete elements at indices 1 and 2 from slice `s`, and the modified slice is printed.
   - A new slice `s2` is declared and assigned the value of slice `s`.
   - The third element of slice `s` (index 2) is modified to "Chai Latte".
   - Both slices `s` and `s2` are printed to observe the change. Both slices reflect the modification made to slice `s`.

Output:
```
[]
[Coffee Espresso Cappuccino]
Espresso
[Coffee Chai Tea Cappuccino]
[Coffee Chai Tea Cappuccino Hot Chocolate Hot Tea]
[Coffee Cappuccino Hot Chocolate Hot Tea]
[Coffee Cappuccino Chai Latte Hot Chocolate Hot Tea] [Coffee Cappuccino Chai Latte Hot Chocolate Hot Tea]
```

This code shows different things you can do with slices in Go. Slices are like lists in other programming languages. You can do things like create them, change what's inside them, add new stuff to them, take things out of them, and copy them.
- It starts by creating a slice, which is like a list, and prints it out.
- Then, it changes something inside the slice and prints it again.
- After that, it adds something new to the slice and prints it again.
- Next, it removes something from the slice and prints it again.
- Finally, it copies the slice and prints both the original and the copy to show they are separate but have the same content.

# Maps

```go
package main

import (
	"fmt"
)

func main() {
	// Declare a map variable m with keys of type string and values of type slice of string
	var m map[string][]string
	fmt.Println("Initial map:", m) // Output: Initial map: map[]

	// Initialize map m with key-value pairs
	m = map[string][]string{
		"coffee": {"Coffee", "Espresso", "Cappuccino"},
		"tea":    {"Hot Tea", "Chai Tea", "Chai Latte"},
	}

	fmt.Println("Map after initialization:", m) // Output: Map after initialization: map[coffee:[Coffee Espresso Cappuccino] tea:[Hot Tea Chai Tea Chai Latte]]

	// Access and print the value associated with the key "coffee"
	fmt.Println("Values for 'coffee':", m["coffee"]) // Output: Values for 'coffee': [Coffee Espresso Cappuccino]

	// Delete the key-value pair with key "tea"
	delete(m, "tea")
	fmt.Println("Map after deletion:", m) // Output: Map after deletion: map[coffee:[Coffee Espresso Cappuccino]]

	// Add a new key-value pair to the map
	m["other"] = []string{"Hot Chocolate"}
	fmt.Println("Map after addition:", m) // Output: Map after addition: map[coffee:[Coffee Espresso Cappuccino] other:[Hot Chocolate]]

	// Accessing a non-existent key "tea"
	fmt.Println("Values for 'tea':", m["tea"]) // Output: Values for 'tea': []

	// Check if a key "tea" exists in the map
	v, ok := m["tea"]
	fmt.Println("Value for 'tea':", v, "Existence:", ok) // Output: Value for 'tea': [] Existence: false

	// Assigning map m to another map variable m2
	m2 := m
	// Modify the value associated with the key "coffee" in map m2
	m2["coffee"] = []string{"Coffee"}
	// Modify the value associated with the key "tea" in map m
	m["tea"] = []string{"Hot Tea"}

	fmt.Println("Map m after modification:", m)   // Output: Map m after modification: map[coffee:[Coffee] other:[Hot Chocolate] tea:[Hot Tea]]
	fmt.Println("Map m2 after modification:", m2) // Output: Map m2 after modification: map[coffee:[Coffee] other:[Hot Chocolate] tea:[Hot Tea]]
}
```

**Output:**

```
Initial map: map[]
Map after initialization: map[coffee:[Coffee Espresso Cappuccino] tea:[Hot Tea Chai Tea Chai Latte]]
Values for 'coffee': [Coffee Espresso Cappuccino]
Map after deletion: map[coffee:[Coffee Espresso Cappuccino]]
Map after addition: map[coffee:[Coffee Espresso Cappuccino] other:[Hot Chocolate]]
Values for 'tea': []
Value for 'tea': [] Existence: false
Map m after modification: map[coffee:[Coffee] other:[Hot Chocolate] tea:[Hot Tea]]
Map m2 after modification: map[coffee:[Coffee] other:[Hot Chocolate] tea:[Hot Tea]]
```

**Explanation:**
This program is about using maps in Go. A map is like a dictionary where each item has a key and a value. 

- At the beginning, a map called `m` is made, but it's empty. We print it out, so it shows nothing.
- Then, we add some key-value pairs to the map. The keys are words, and the values are lists of words.
- Next, we do different things with the map like getting items by their key, removing items, adding new items, and checking if a key exists.
- Finally, we show that if you copy a map into another one, they both point to the same information. So if you change something in one map, it changes in the other map too.

# Struct


```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

func main() {
	// Print initial message
	fmt.Println("Please select an option")
	fmt.Println("1) Print menu")

	// Read user input
	in := bufio.NewReader(os.Stdin)
	choice, _ := in.ReadString('\n')
	choice = strings.TrimSpace(choice) // We don't know what to do with this yet!

	// Define a struct for menu items
	type menuItem struct {
		name   string
		prices map[string]float64
	}

	// Define menu items with their respective prices
	menu := []menuItem{
		{name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
		{name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
	}

	// Print the menu
	fmt.Println(menu)
}
```


**Output**:

```
Please select an option
1) Print menu
[{Coffee map[large:1.95 medium:1.8 small:1.65]} {Espresso map[double:2.25 single:1.9 triple:2.55]}]
```


**Explanation**:

- The program starts by printing a message prompting the user to select an option and printing the option to print the menu.

- It then reads the user's input using `bufio.NewReader(os.Stdin)` to create a reader to read from standard input, and `ReadString('\n')` to read until the user presses Enter. The input is stored in the variable `choice`.

- `strings.TrimSpace(choice)` is used to remove any leading or trailing whitespace from the user's input. However, at this stage of the code, we haven't implemented what to do with the user's choice yet.

- A custom type `menuItem` is defined, which represents a menu item. It has two fields: `name` (string) representing the name of the item and `prices` (map[string]float64) representing the prices of the item for different sizes or options.

- An array `menu` of `menuItem` structs is defined, containing two menu items: "Coffee" and "Espresso", each with their respective prices for different options.

- Finally, the program prints the entire menu array.



# Variables

```go
package main

import "fmt"

func main() {
    // Declare a variable 'a' of type string and assign the value "foo" to it
    var a string
    a = "foo"

    // Print the value of variable 'a'
    fmt.Println(a)

    // Declare a variable 'b' of type int and assign the value 99 to it
    var b int = 99
    // Print the value of variable 'b'
    fmt.Println(b)

    // Declare a variable 'c' and let Go infer its type as bool, and assign the value true to it
    var c = true
    // Print the value of variable 'c'
    fmt.Println(c)

    // Declare a variable 'd' and let Go infer its type as float64, and assign the value 3.1415 to it
    d := 3.1415
    // Print the value of variable 'd'
    fmt.Println(d)

    // Convert the value of 'd' to an integer and assign it to variable 'e'
    var e int = int(d)
    // Print the value of variable 'e'
    fmt.Println(e)
}
```

**Output:**
```
foo
99
true
3.1415
3
```

**Explanation:**

1. In this Go program, we declare and initialize variables of different types and print their values.

2. `var a string` declares a variable `a` of type string. We assign the value "foo" to `a` using `a = "foo"`.

3. `fmt.Println(a)` prints the value of `a`, which is "foo".

4. `var b int = 99` declares a variable `b` of type int and assigns it the value 99.

5. `fmt.Println(b)` prints the value of `b`, which is 99.

6. `var c = true` declares a variable `c` without explicitly specifying its type. Go infers the type of `c` as bool based on the assigned value true.

7. `fmt.Println(c)` prints the value of `c`, which is true.

8. `d := 3.1415` declares a variable `d` and lets Go infer its type as float64. We assign the value 3.1415 to `d`.

9. `fmt.Println(d)` prints the value of `d`, which is 3.1415.

10. `var e int = int(d)` converts the value of `d` to an integer and assigns it to variable `e`.

11. `fmt.Println(e)` prints the value of `e`, which is the truncated integer part of the value stored in `d`, in this case, 3.







# Arithmetic Operations

This Go program demonstrates basic arithmetic operations such as addition, subtraction, multiplication, division, and modulus. It also showcases type conversion and comparison operators.

```go
package main

import "fmt"

func main() {
    // Declaring two integer variables
    a, b := 5, 2

    // Addition
    fmt.Println(a + b)

    // Subtraction
    fmt.Println(a - b)

    // Multiplication
    fmt.Println(a * b)

    // Integer division (result is an integer)
    fmt.Println(a / b)

    // Modulus (remainder of integer division)
    fmt.Println(a % b)

    // Float division (result is a floating-point number)
    fmt.Println(float32(a) / float32(b))

    // Comparison operators
    fmt.Println(a == b) // Equal to
    fmt.Println(a < b)  // Less than
    fmt.Println(a > b)  // Greater than
}
```

Output:
```
7
3
10
2
1
2.5
false
false
true
```

Explanation:
- The program begins by declaring two integer variables `a` and `b` with values 5 and 2, respectively.
- It then performs various arithmetic operations:
  - Addition (`a + b`): 5 + 2 = 7
  - Subtraction (`a - b`): 5 - 2 = 3
  - Multiplication (`a * b`): 5 * 2 = 10
  - Integer division (`a / b`): 5 / 2 = 2 (integer division truncates the decimal part)
  - Modulus (`a % b`): 5 % 2 = 1 (remainder of 5 divided by 2)
  - Float division (`float32(a) / float32(b)`): 5.0 / 2.0 = 2.5 (explicit type conversion to float32)
- Finally, it demonstrates comparison operators:
  - Equal to (`a == b`): 5 is not equal to 2, so it prints `false`
  - Less than (`a < b`): 5 is not less than 2, so it prints `false`
  - Greater than (`a > b`): 5 is greater than 2, so it prints `true`

 
# Constants
This Go program demonstrates the usage of constants and the `iota` identifier.

```go
package main

import "fmt"

func main() {
    // Constants with explicit types
    const a = 42
    const b float32 = 3

    // Assigning constants to variables with compatible types
    var i int = a
    fmt.Println(i)
    var f32 float32 = a
    fmt.Println(f32)

    // Assigning constant 'b' to variable 'f32'
    f32 = b
    fmt.Println(f32)

    // iota usage in constant declarations
    const c = iota
    fmt.Println(c)

    // Using iota in a const block
    const (
        d = 2 * 5
        e     // e = 2 * 5 (implicitly)
        f = iota  // f = 0
        g         // g = 1 (incremented from iota)
        h = 10 * iota  // h = 10 * 2
    )

    // Printing values of constants
    fmt.Println(d, e, f, g, h)
}
```

### Output

```
42
42
3
0
10 10 0 1 20
```

### Explanation

1. Constants `a` and `b` are declared with values `42` and `3` respectively. `a` is untyped, and `b` is explicitly typed as `float32`.
2. Constant `a` is assigned to variable `i` of type `int`, and `f32` of type `float32`. Go allows this because the values are compatible.
3. Constant `b` is assigned to variable `f32`.
4. The `iota` identifier is used to generate sequential integer values in a const block. In this case, `c` is assigned the value `0`.
5. In the second const block, `d` is assigned the value `2 * 5`, `e` implicitly gets the same value as `d`, `f` is assigned `iota` (which starts at `0`), `g` gets the next value of `iota`, and `h` is assigned `10 * iota`.
6. The values of all constants are printed using `fmt.Println()`.


# Pointers

```go
package main

import "fmt"

func main() {
    // Define a string variable
    s := "Hello, world!"

    // Create a pointer to the string variable
    p := &s

    // Print the memory address stored in the pointer
    fmt.Println(p)

    // Dereference the pointer to access the value it points to
    fmt.Println(*p)

    // Modify the value indirectly through the pointer
    *p = "Hello, Gophers!"

    // Print the original string and the modified string
    fmt.Println(s, *p)

    // Create a new pointer to a string
    p = new(string)

    // Print the memory address stored in the new pointer and its value
    fmt.Println(p, *p)
}
```

### Output:
```
0xc000010200
Hello, world!
Hello, Gophers! Hello, Gophers!
0xc000010220 
```

### Explanation:

1. **Variable Declaration**: 
   - `s` is declared as a string variable with the value `"Hello, world!"`.

2. **Pointer Creation**:
   - `p` is declared as a pointer to a string (`*string`).
   - `&s` assigns the memory address of the variable `s` to the pointer `p`.

3. **Printing the Pointer**:
   - `fmt.Println(p)` prints the memory address stored in the pointer `p`.

4. **Dereferencing the Pointer**:
   - `fmt.Println(*p)` dereferences the pointer `p`, i.e., it accesses the value stored at the memory address pointed to by `p` and prints it.

5. **Modifying Value via Pointer**:
   - `*p = "Hello, Gophers!"` modifies the value indirectly through the pointer `p`. It changes the value of the variable `s` to `"Hello, Gophers!"`.

6. **Printing Original and Modified Values**:
   - `fmt.Println(s, *p)` prints both the original value of `s` and the modified value (pointed to by `p`).

7. **Creating a New Pointer**:
   - `p = new(string)` creates a new pointer to a string and assigns its memory address to `p`.

8. **Printing New Pointer**:
   - `fmt.Println(p, *p)` prints the memory address stored in the new pointer `p` (which is different from the previous pointer) and its zero-initialized value (empty string in this case).

This code demonstrates the basic concepts of pointers in Go, including creating pointers, accessing values through pointers, modifying values indirectly via pointers, and creating new pointers using the `new` function.


# Demo CLI Program For Text Input Uppercase Converter

This Go program prompts the user to input text, reads the input from the standard input (keyboard), converts it to uppercase, removes any leading or trailing whitespace, and then prints the modified text with an exclamation mark appended.

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

func main() {
	// Print prompt message
	fmt.Println("Insert Text")

	// Create a new buffered reader to read from standard input
	in := bufio.NewReader(os.Stdin)

	// Read a string from standard input until a newline character is encountered
	s, _ := in.ReadString('\n')

	// Remove leading and trailing whitespace from the input string
	s = strings.TrimSpace(s)

	// Convert the input string to uppercase
	s = strings.ToUpper(s)

	// Print the modified string with an exclamation mark appended
	fmt.Println(s + "!")
}
```

**Output:**
```
Insert Text
hi, my name is saklain
HI, MY NAME IS SAKLAIN!
```

**Explanation:**

1. **Prompt Message**: The program prints "Insert Text" to prompt the user to input text.

2. **Input Reading**: It creates a buffered reader `in` to read from the standard input (`os.Stdin`).

3. **Reading String**: The `ReadString('\n')` function reads a string from the standard input until it encounters a newline character ('\n'). The read string is stored in the variable `s`.

4. **Trimming Whitespace**: The `strings.TrimSpace()` function removes any leading or trailing whitespace from the input string `s`. This ensures that any extraneous whitespace entered by the user is removed.

5. **Uppercase Conversion**: The `strings.ToUpper()` function converts the input string `s` to uppercase. This ensures that the entire string is in uppercase characters.

6. **Printing Modified String**: Finally, the modified string `s` is printed to the standard output (`os.Stdout`) with an exclamation mark appended (`+ "!"`). This displays the converted uppercase string to the user.
## Working of the above CLI.
1. The program starts with a `package main` declaration, indicating that this is the main package that can be compiled into an executable program.

2. The required packages are imported:
   - `bufio`: This package implements buffered I/O and provides convenient functions for reading input.
   - `fmt`: This package implements formatted I/O and provides functions for printing and formatting input and output.
   - `os`: This package provides a platform-independent interface to operating system functionality, including access to standard input, standard output, and standard error.
   - `strings`: This package provides functions for manipulating strings.

3. The `main()` function is defined, which is the entry point of the program.

4. It prints "Insert Text" to the standard output.

5. It creates a new `bufio.Reader` called `in`, which reads from the standard input (`os.Stdin`).

6. It uses `in.ReadString('\n')` to read a string from the standard input until it encounters a newline (`'\n'`). It returns the string read and an error, but the error is ignored in this case (using `_`).

7. The read string `s` is then trimmed of any leading or trailing whitespace using `strings.TrimSpace(s)`.

8. The trimmed string is converted to uppercase using `strings.ToUpper(s)`.

9. Finally, the uppercase string is concatenated with an exclamation mark (`"!"`) and printed to the standard output using `fmt.Println()`.

So, when you run this program, it will print "Insert Text" and then wait for you to input a string. After you input a string and press Enter, it will convert that string to uppercase, trim any leading or trailing whitespace, append an exclamation mark to it, and then print the modified string with the exclamation mark.



# Demo Web Service Program for Serving Menu Text Using HTTP Server.

Code Explanation:
1. We begin by importing necessary packages:
   - `io`: Provides basic interfaces to I/O primitives.
   - `net/http`: Provides HTTP client and server implementations.
   - `os`: Provides operating system functionalities.

2. We define the `main()` function, which is the entry point of the program.
   - We register a handler function, `Handler`, to handle incoming HTTP requests at the root path ("/").
   - We start an HTTP server listening on port 3000 using `http.ListenAndServe()`.

3. We define the `Handler` function to handle HTTP requests.
   - Inside the handler function, we open the "menu.txt" file for reading.
   - We use `io.Copy()` to copy the contents of the file to the `http.ResponseWriter`, which sends the contents of the file back to the client who made the HTTP request.

4. The contents of the "menu.txt" file represent a menu with different items listed.

Program:
```go
package main

import (
	"io"
	"net/http"
	"os"
)

func main() {
	http.HandleFunc("/", Handler)
	http.ListenAndServe(":3000", nil)

}

func Handler(w http.ResponseWriter, r *http.Request) {
	f, _ := os.Open("menu.txt")

	io.Copy(w, f)
}
```

Text file (menu.txt):
```
Coffee
Espresso
Cappuccino

Hot Tea
Chai Tea
Chai Latte

Hot Chocolate
```

Output:
When you run this program and access http://localhost:3000 in your browser or send an HTTP request to this URL using a tool like cURL, it will display the contents of the "menu.txt" file, which is served by the Go HTTP server. The output will be the menu items listed in the text file, exactly as they appear in the file:

```
Coffee
Espresso
Cappuccino

Hot Tea
Chai Tea
Chai Latte

Hot Chocolate
```



# Basic Loops

```go
package main

import (
	"fmt"
)

func main() {
	// Part 1: Loop with a break
	i := 99
	for {
		fmt.Println(i)
		i += 1
		break
	}

	// Part 2: Loop with a condition
	i = 5
	for i < 10 {
		fmt.Println(i)
		i++
	}

	// Part 3: Loop with initialization, condition, and post statement
	for i := 0; i < 10; i++ {
		fmt.Println(i)
	}
}
```

Explanation:
1. **Part 1**: In this section, a `for` loop is used without any condition. It continues indefinitely until a `break` statement is encountered. Inside the loop, the variable `i` is printed, incremented by 1, and then the loop is exited with `break`.

2. **Part 2**: This section demonstrates a `for` loop with a condition (`i < 10`). The loop continues executing as long as the condition (`i < 10`) is true. Inside the loop, the value of `i` is printed, incremented by 1, and the loop continues until `i` becomes equal to or greater than 10.

3. **Part 3**: Here, a typical `for` loop construct with initialization (`i := 0`), condition (`i < 10`), and post statement (`i++`) is used. The loop initializes `i` to 0, continues as long as `i` is less than 10, increments `i` by 1 in each iteration, and prints the value of `i`.

Output:
```
99
5
6
7
8
9
0
1
2
3
4
5
6
7
8
9
```

In the output, you can see:
- The initial value of `i` is printed in the first loop (`99`).
- In the second loop, the values of `i` from `5` to `9` are printed.
- In the third loop, the values of `i` from `0` to `9` are printed again.



# Looping Over Collection
## Before


Program:
```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

func main() {
	fmt.Println("Please select an option")
	fmt.Println("1) Print menu")
	in := bufio.NewReader(os.Stdin)
	choice, _ := in.ReadString('\n')
	choice = strings.TrimSpace(choice) // we don't know what to do with this yet!

	type menuItem struct {
		name   string
		prices map[string]float64
	}

	menu := []menuItem{
		{name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
		{name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
	}

	fmt.Println(menu)
}
```


Output:
```
Please select an option
1) Print menu
[{Coffee map[small:1.65 medium:1.8 large:1.95]} {Espresso map[single:1.9 double:2.25 triple:2.55]}]
```

Explanation:
- This Go program displays a simple menu and allows the user to select an option.
- It first prints a prompt asking the user to select an option.
- Then, it reads the user's input using `bufio.NewReader(os.Stdin)`.
- The user's input is stored in the variable `choice`.
- The `strings.TrimSpace()` function is used to remove any leading or trailing whitespace from the user's input. Currently, there is no action based on the user's choice, so this line is a placeholder.
- Next, a custom type `menuItem` is defined, representing an item in the menu. It contains the name of the item and a map of prices for different sizes or options.
- The menu is defined as a slice of `menuItem` structs, with each item having a name and a map of prices.
- Finally, the program prints the menu using `fmt.Println(menu)`.

The output displays the menu items along with their respective prices in a structured format.

## After

This Go program presents an interactive menu where the user can select an option. If the user chooses to print the menu, it displays a list of items along with their sizes and prices.

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

func main() {
	// Prompt the user to select an option
	fmt.Println("Please select an option")
	fmt.Println("1) Print menu")

	// Read the user's choice from standard input
	in := bufio.NewReader(os.Stdin)
	choice, _ := in.ReadString('\n')

	// Remove leading/trailing whitespace from the choice
	choice = strings.TrimSpace(choice) // we don't know what to do with this yet!

	// Define a struct to represent menu items
	type menuItem struct {
		name   string            // Name of the item
		prices map[string]float64 // Prices for different sizes
	}

	// Define the menu items
	menu := []menuItem{
		{name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
		{name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
	}

	// Print the menu
	for _, item := range menu {
		fmt.Println(item.name)
		fmt.Println(strings.Repeat("-", 10))
		for size, cost := range item.prices {
			fmt.Printf("\t%10s%10.2f\n", size, cost)
		}
	}
}
```

**Output:**
```
Please select an option
1) Print menu
Coffee
----------
	    small      1.65
	   medium      1.80
	    large      1.95
Espresso
----------
	   single      1.90
	   double      2.25
	  triple      2.55
```

**Explanation:**
- The program starts by prompting the user to select an option and prints the option to print the menu.
- It reads the user's choice from the standard input.
- The `strings.TrimSpace()` function is used to remove any leading or trailing whitespace from the user's choice. Currently, there's no functionality implemented based on the user's choice, so it's not utilized further.
- The program defines a struct named `menuItem`, which represents a menu item. It has two fields: `name` for the name of the item and `prices` for a map of prices for different sizes.
- The program then defines a slice named `menu` containing various `menuItem` structs representing different items on the menu along with their prices for different sizes.
- It iterates over each item in the `menu` slice and prints the name of the item followed by a series of dashes.
- For each item, it iterates over the prices map and prints each size along with its corresponding price.


Looping over a collection before and after each change can have significant differences in terms of the behavior and outcomes of the loop.

1. **Looping Over Collection Before Making Changes:**
   - When you loop over a collection before making changes, you're essentially iterating over the original state of the collection.
   - Any modifications made to the collection during the loop iteration won't affect the current iteration. This means that you're not modifying the collection you're iterating over, but rather perhaps creating a new collection based on the original one.
   - This approach is often used when you want to analyze or process the existing data without altering it directly.

2. **Looping Over Collection After Making Changes:**
   - When you loop over a collection after making changes, you're working with the modified state of the collection.
   - Any modifications made to the collection during the loop iteration will impact the current iteration, potentially altering the behavior of the loop.
   - This approach is often used when you need to perform operations that involve modifying the collection itself, such as removing elements that meet certain conditions or updating values based on specific criteria.

In simple terms, looping over a collection before making changes allows you to inspect the original data without affecting it, while looping over a collection after making changes enables you to apply modifications directly to the collection as you iterate over it.
