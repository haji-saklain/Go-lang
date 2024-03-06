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





# if Statements

```go
package main

import (
	"fmt"
)

func main() {
    // Defining a variable i with value 5 in a short declaration within the if statement
	if i := 5; i < 5 { // Check if i is less than 5
		fmt.Println("i is less than 5")
	} else if i < 10 { // If i is not less than 5, check if i is less than 10
		fmt.Println("i is less than 10")
	} else { // If i is not less than 5 and not less than 10, then it must be greater than or equal to 10
		fmt.Println("i is greater than or equal to 10")
	}
}
```
Output:
```
i is less than 10
```

In this output, the program prints "i is less than 10" because the value of `i` is 5, which satisfies the condition `i < 10`.

Explanation:
- In this Go program, we're using conditional statements (`if`, `else if`, `else`) to check the value of the variable `i`.
- We're also using a short declaration syntax (`:=`) to declare and initialize `i` with a value of 5 within the `if` statement.
- The first `if` statement checks if `i` is less than 5. If it is, it prints "i is less than 5".
- If `i` is not less than 5, the program proceeds to the `else if` statement, which checks if `i` is less than 10. If it is, it prints "i is less than 10".
- If `i` is neither less than 5 nor less than 10, the program goes to the `else` block and prints "i is greater than or equal to 10".

# Switches
## before

```go
package main

import (
	"fmt"
	"strings"
)

func main() {
	fmt.Println("Please select an option")
	fmt.Println("1) Print menu")
	var choice string
	fmt.Scan(&choice) // we don't know what to do with this yet!

	type menuItem struct {
		name   string
		prices map[string]float64
	}

	menu := []menuItem{
		{name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
		{name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
	}

	for _, item := range menu {
		fmt.Println(item.name)
		fmt.Println(strings.Repeat("-", 10))
		for size, cost := range item.prices {
			fmt.Printf("\t%10s%10.2f\n", size, cost)
		}
	}
}
```

Explanation:

1. The program starts by printing a message asking the user to select an option.
2. It then prints an option to print the menu (option 1), but it doesn't handle this choice yet.
3. It defines a struct `menuItem` which represents an item on the menu. Each item has a name and a map of sizes to prices.
4. It creates a slice `menu` of `menuItem` structs, representing the coffee items available on the menu along with their prices.
5. It iterates over each item in the `menu` slice.
   - For each item, it prints the name of the item.
   - It prints a line of dashes to separate the name from the prices.
   - It iterates over each size and price pair in the `prices` map for the item, printing the size and corresponding price formatted neatly.

Output:

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

This output displays the coffee shop menu with the available items (Coffee and Espresso) along with their respective sizes and prices.


## after

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

// Define a struct to represent a menu item
type menuItem struct {
	name   string            // Name of the menu item
	prices map[string]float64 // Prices of the item for different sizes
}

func main() {
	// Initialize the menu with some predefined items
	menu := []menuItem{
		{name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
		{name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
	}

	// Create a reader to read user input from the standard input
	in := bufio.NewReader(os.Stdin)

	// Loop to continuously prompt the user for options until they choose to quit
loop:
	for {
		fmt.Println("Please select an option")
		fmt.Println("1) Print menu")
		fmt.Println("2) Add item")
		fmt.Println("q) Quit")
		choice, _ := in.ReadString('\n')

		switch strings.TrimSpace(choice) {
		case "1":
			// Print the menu items and their prices
			for _, item := range menu {
				fmt.Println(item.name)
				fmt.Println(strings.Repeat("-", len(item.name)))
				for size, cost := range item.prices {
					fmt.Printf("\t%10s%10.2f\n", size, cost)
				}
			}
		case "2":
			// Add a new item to the menu
			fmt.Println("Please enter the name of the new item")
			name, _ := in.ReadString('\n')
			// Trim whitespace from the input and add the new item to the menu
			menu = append(menu, menuItem{name: strings.TrimSpace(name), prices: make(map[string]float64)})
		case "q":
			// Exit the loop and end the program
			break loop
		default:
			fmt.Println("Unknown option")
		}
	}
}
```

To run this program, save it in a file named `menu_management.go` and execute it using the Go compiler (`go run menu_management.go`).

Explanation:
- The program defines a struct `menuItem` to represent a menu item, which contains the name of the item and a map of prices for different sizes.
- It initializes a slice `menu` with some predefined menu items.
- It continuously prompts the user for options using a loop, allowing them to print the menu or add new items.
- When the user chooses to print the menu, it iterates over the menu items and their prices, printing them to the console.
- When the user chooses to add a new item, it prompts them for the name of the item and adds it to the menu.
- The program continues to run until the user chooses to quit.

Here's a sample output of the program:

```
Please select an option
1) Print menu
2) Add item
q) Quit
1
Coffee
------
     small      1.65
    medium      1.80
     large      1.95
Espresso
--------
    single      1.90
    double      2.25
    triple      2.55
Please select an option
1) Print menu
2) Add item
q) Quit
2
Please enter the name of the new item
Tea
Please select an option
1) Print menu
2) Add item
q) Quit
1
Coffee
------
     small      1.65
    medium      1.80
     large      1.95
Espresso
--------
    single      1.90
    double      2.25
    triple      2.55
     Tea
------
Please select an option
1) Print menu
2) Add item
q) Quit
q
```

This demonstrates adding a new item "Tea" to the menu and then printing the updated menu before quitting the program.



## Deferred Functions:
In Go, a deferred function is a function call that is executed just before the surrounding function returns. These deferred function calls are executed in Last In, First Out (LIFO) order. They are often used for cleanup tasks or actions that should be performed regardless of how the function exits (either normally or due to a panic).

```go
package main

import (
	"fmt"
)

func main() {
	fmt.Println("main 1")
	defer fmt.Println("defer 1")
	fmt.Println("main 2")
	defer fmt.Println("defer 2")

	// Some other code (commented out)
	// db, _ := sql.Open("driverName", "connection string")
	// defer db.Close()

	// rows, _ := db.Query("some sql query here")
	// defer rows.Close()
}
```

1. **`fmt.Println("main 1")`:** This line prints "main 1" to the console.

2. **`defer fmt.Println("defer 1")`:** This line defers the execution of `fmt.Println("defer 1")` until the surrounding function (`main()`) is about to return. So, "defer 1" will be printed just before `main()` exits.

3. **`fmt.Println("main 2")`:** This line prints "main 2" to the console.

4. **`defer fmt.Println("defer 2")`:** Similar to the previous deferred function, this defers the execution of `fmt.Println("defer 2")` until the surrounding function (`main()`) is about to return. So, "defer 2" will be printed just before `main()` exits.

5. The commented-out code represents examples of using deferred functions in other scenarios, such as closing a database connection (`db.Close()`) or closing database rows (`rows.Close()`). These deferred calls ensure that resources are properly released when the function exits, regardless of whether it exits normally or due to an error.


```
main 1
main 2
defer 2
defer 1
```

Explanation:
- "main 1" and "main 2" are printed as expected when their respective `fmt.Println()` calls are executed.
- "defer 2" is printed just before the `main()` function exits because it was deferred earlier.
- "defer 1" is printed after "defer 2" because it was deferred later and hence executed first in the Last In, First Out (LIFO) order.



# Panic and Recover

```go
package main

import "fmt"

func main() {
    dividend, divisor := 10, 5
    fmt.Printf("%v divided by %v is %v\n", dividend, divisor, divide(dividend, divisor))

    dividend, divisor = 10, 0
    fmt.Printf("%v divided by %v is %v\n", dividend, divisor, divide(dividend, divisor))
}

func divide(dividend, divisor int) int {
    return dividend / divisor
}
```

Output:
```
10 divided by 5 is 2
panic: runtime error: integer divide by zero
```

Explanation:
- In the first part of the code, we have a `divide` function that performs integer division of two numbers (`dividend` by `divisor`). It doesn't handle the case when the divisor is 0.
- In the `main` function, we call `divide` twice: first with `dividend=10` and `divisor=5`, and then with `dividend=10` and `divisor=0`.
- The first call to `divide` completes successfully, printing "10 divided by 5 is 2".
- However, the second call to `divide` results in a runtime error because we're trying to divide by zero. This error causes the program to panic, which means it abruptly terminates with an error message.

Now, let's modify the program to handle the panic using `recover`:

```go
package main

import "fmt"

func main() {
    dividend, divisor := 10, 5
    fmt.Printf("%v divided by %v is %v\n", dividend, divisor, divide(dividend, divisor))

    dividend, divisor = 10, 0
    fmt.Printf("%v divided by %v is %v\n", dividend, divisor, divide(dividend, divisor))
}

func divide(dividend, divisor int) int {
    defer func() {
        if recover() != nil {
            fmt.Println("Panic detected!")
        }
    }()
    return dividend / divisor
}
```

Output:
```
10 divided by 5 is 2
Panic detected!
0 divided by 0 is 0
```

Explanation:
- In this modified version, we use the `defer` statement to set up a function call (`recover`) to be executed when the `divide` function exits.
- Inside the `defer` function, we check if `recover()` returns a non-nil value. If it does, it means a panic occurred, and we print "Panic detected!".
- Now, when the program encounters the division by zero error, it panics as before. However, this time the panic is caught by the `recover` function inside the `divide` function, preventing the program from terminating abruptly. Instead, it prints "Panic detected!" and continues executing the rest of the code.
- As a result, the program continues to execute, printing "0 divided by 0 is 0" after handling the panic.





# Functions

**Before:**

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

type menuItem struct {
	name   string
	prices map[string]float64
}

var menu = []menuItem{
	{name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
	{name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
}

var in = bufio.NewReader(os.Stdin)

func main() {

loop:
	for {
		fmt.Println("Please select an option")
		fmt.Println("1) Print menu")
		fmt.Println("2) Add item")
		fmt.Println("q) quit")
		choice, _ := in.ReadString('\n')

		switch strings.TrimSpace(choice) {
		case "1":
			for _, item := range menu {
				fmt.Println(item.name)
				fmt.Println(strings.Repeat("-", 10))
				for size, cost := range item.prices {
					fmt.Printf("\t%10s%10.2f\n", size, cost)
				}
			}
		case "2":
			fmt.Println("Please enter the name of the new item")
			name, _ := in.ReadString('\n')
			menu = append(menu, menuItem{name: strings.TrimSpace(name), prices: make(map[string]float64)})
		case "q":
			break loop
		default:
			fmt.Println("Unknown option")
		}
	}

}
```

**Output:**
```
Please select an option
1) Print menu
2) Add item
q) quit
1
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
Please select an option
1) Print menu
2) Add item
q) quit
2
Please enter the name of the new item
Mocha
Please select an option
1) Print menu
2) Add item
q) quit
q
```

**Explanation:**
- The program defines a `menuItem` struct representing items on the menu, which includes a name and a map of sizes to prices.
- It initializes a slice `menu` containing some pre-defined items.
- It uses a loop to continuously prompt the user for options until they choose to quit (`q`).
- Within the loop, it presents options to print the menu (`1`), add a new item (`2`), or quit.
- Depending on the user's choice, it either prints the menu with prices, prompts for a new item's name and adds it to the menu, or quits the program.
- The printing of the menu is done directly inside the `main` function.

**After:**

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

type menuItem struct {
	name   string
	prices map[string]float64
}

var menu = []menuItem{
	{name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
	{name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
}

var in = bufio.NewReader(os.Stdin)

func main() {

loop:
	for {
		fmt.Println("Please select an option")
		fmt.Println("1) Print menu")
		fmt.Println("2) Add item")
		fmt.Println("q) quit")
		choice, _ := in.ReadString('\n')

		switch strings.TrimSpace(choice) {
		case "1":
			printMenu()
		case "2":
			addItem()
		case "q":
			break loop
		default:
			fmt.Println("Unknown option")
		}
	}
}

func printMenu() {
	for _, item := range menu {
		fmt.Println(item.name)
		fmt.Println(strings.Repeat("-", 10))
		for size, cost := range item.prices {
			fmt.Printf("\t%10s%10.2f\n", size, cost)
		}
	}
}
func addItem() {
	fmt.Println("Please enter the name of the new item")
	name, _ := in.ReadString('\n')
	menu = append(menu, menuItem{name: strings.TrimSpace(name), prices: make(map[string]float64)})
}
```

**Output:**
```
Please select an option
1) Print menu
2) Add item
q) quit
1
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
Please select an option
1) Print menu
2) Add item
q) quit
2
Please enter the name of the new item
Mocha
Please select an option
1) Print menu
2) Add item
q) quit
q
```

**Explanation:**
- The code has been refactored to separate concerns by moving the functionality for printing the menu and adding an item into their respective functions `printMenu()` and `addItem()`.
- This makes the code more modular and easier to understand, as each function now has a single responsibility.
- The `main()` function now simply presents options to the user and calls the appropriate function based on their choice.
- The `printMenu()` function is responsible for printing the menu with prices.
- The `addItem()` function prompts the user for a new item's name and adds it to the menu.


# Packages

This Go program implements a simple menu management system that allows users to view the menu items and prices, add new items to the menu, or quit the program.

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

// Define a struct for menu items
type menuItem struct {
	name   string            // Name of the item
	prices map[string]float64 // Prices for different sizes
}

// Define the initial menu
var menu = []menuItem{
	{name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
	{name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
}

// Create a reader for user input
var in = bufio.NewReader(os.Stdin)

func main() {
	// Main loop for menu options
loop:
	for {
		fmt.Println("Please select an option")
		fmt.Println("1) Print menu")
		fmt.Println("2) Add item")
		fmt.Println("q) quit")
		choice, _ := in.ReadString('\n')

		// Process user choice
		switch strings.TrimSpace(choice) {
		case "1":
			printMenu()
		case "2":
			addItem()
		case "q":
			break loop
		default:
			fmt.Println("Unknown option")
		}
	}
}

// Function to print the menu
func printMenu() {
	for _, item := range menu {
		fmt.Println(item.name)
		fmt.Println(strings.Repeat("-", 10))
		for size, cost := range item.prices {
			fmt.Printf("\t%10s%10.2f\n", size, cost)
		}
	}
}

// Function to add a new item to the menu
func addItem() {
	fmt.Println("Please enter the name of the new item")
	name, _ := in.ReadString('\n')
	menu = append(menu, menuItem{name: strings.TrimSpace(name), prices: make(map[string]float64)})
}
```

#### Output:
```
Please select an option
1) Print menu
2) Add item
q) quit
1
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
Please select an option
1) Print menu
2) Add item
q) quit
2
Please enter the name of the new item
Tea
Please select an option
1) Print menu
2) Add item
q) quit
1
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
Tea
----------
Please select an option
1) Print menu
2) Add item
q) quit
q
```

In this program, the user can choose from three options:
1. Print the menu
2. Add a new item to the menu
3. Quit the program





### Program 1: Main Program

```go
package main

import (
    "bufio"
    "demo/menu" // Importing package "menu"
    "fmt"
    "os"
    "strings"
)

var in = bufio.NewReader(os.Stdin)

func main() {
    loop:
    for {
        fmt.Println("Please select an option")
        fmt.Println("1) Print menu")
        fmt.Println("2) Add item")
        fmt.Println("q) quit")
        choice, _ := in.ReadString('\n')

        switch strings.TrimSpace(choice) {
        case "1":
            menu.Print() // Calling function Print() from package "menu"
        case "2":
            menu.Add()   // Calling function Add() from package "menu"
        case "q":
            break loop
        default:
            fmt.Println("Unknown option")
        }
    }
}
```

#### Output:
The output of this program will depend on the user's input. It will display a menu of options, allowing the user to print the menu, add an item to the menu, or quit the program.

---

### Program 2: Data

```go
package menu

// Define a struct type menuItem
type menuItem struct {
    name   string
    prices map[string]float64
}

// Define some initial menu items
var menu = []menuItem{
    {name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
    {name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
}
```

#### Output:
No output is generated from this code. It simply declares the initial data structure for the menu.

---

### Program 3: Menu

```go
package menu

import (
    "bufio"
    "fmt"
    "os"
    "strings"
)

var in = bufio.NewReader(os.Stdin)

// Print function to display the menu
func Print() {
    for _, item := range menu {
        fmt.Println(item.name)
        fmt.Println(strings.Repeat("-", 10))
        for size, cost := range item.prices {
            fmt.Printf("\t%10s%10.2f\n", size, cost)
        }
    }
}

// Add function to add a new item to the menu
func Add() {
    fmt.Println("Please enter the name of the new item")
    name, _ := in.ReadString('\n')
    // Trim any leading or trailing whitespace from the name
    name = strings.TrimSpace(name)
    // Append a new menuItem to the menu slice
    menu = append(menu, menuItem{name: name, prices: make(map[string]float64)})
}
```

#### Output:
The output of this program will be different depending on the user's input. If the user chooses to print the menu, it will display the current items and their prices. If the user chooses to add an item, it will prompt for the name of the new item.



# Methods

### `main.go`

```go
package main

import (
    "bufio"
    "demo/menu"
    "fmt"
    "os"
    "strings"
)

var in = bufio.NewReader(os.Stdin)

func main() {
    loop:
    for {
        fmt.Println("Please select an option")
        fmt.Println("1) Print menu")
        fmt.Println("2) Add item")
        fmt.Println("q) quit")
        choice, _ := in.ReadString('\n')

        switch strings.TrimSpace(choice) {
        case "1":
            menu.Print()
        case "2":
            err := menu.Add()
            if err != nil {
                fmt.Println(fmt.Errorf("invalid input: %w", err))
            }
        case "q":
            break loop
        default:
            fmt.Println("Unknown option")
        }
    }
}
```

**Explanation:**
- This file contains the main program.
- It provides a menu to the user with options to print the menu, add an item, or quit the program.
- It reads user input and calls the appropriate functions from the `menu` package based on the input.

### `menu.go`

```go
package menu

import (
    "bufio"
    "errors"
    "fmt"
    "os"
    "strings"
)

type menuItem struct {
    name   string
    prices map[string]float64
}

var in = bufio.NewReader(os.Stdin)

var menu = []menuItem{
    {name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
    {name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
}

func Print() {
    for _, item := range menu {
        fmt.Println(item.name)
        fmt.Println(strings.Repeat("-", 10))
        for size, cost := range item.prices {
            fmt.Printf("\t%10s%10.2f\n", size, cost)
        }
    }
}

func Add() error {
    fmt.Println("Please enter the name of the new item")
    name, _ := in.ReadString('\n')
    name = strings.TrimSpace(name)

    for _, item := range menu {
        if item.name == name {
            return errors.New("menu item already exists")
        }
    }
    menu = append(menu, menuItem{name: name, prices: make(map[string]float64)})
    return nil
}
```

**Explanation:**
- This file defines the `menu` package.
- It declares a `menuItem` struct to represent menu items.
- It declares a `menu` slice containing sample menu items with their respective prices.
- It provides functions to print the menu (`Print`) and add a new item to the menu (`Add`).

### `data.go`

```go
package menu

var menu = []menuItem{
    {name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
    {name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
}
```

**Explanation:**
- This file declares the initial data for the menu.
- It's included here to demonstrate how data can be separated into its own file for organization.

### Output

When you run the `main.go` program, it will display a menu with options to print the menu, add an item, or quit. Here's an example of the output:

```
Please select an option
1) Print menu
2) Add item
q) quit
```

Depending on the user's input, it will either print the menu, prompt the user to add a new item to the menu, or quit the program. The output will vary based on the user's choices.

# Methods
### `main` Package

```go
package main

import (
	"bufio"
	"demo/menu"
	"fmt"
	"os"
	"strings"
)

var in = bufio.NewReader(os.Stdin)

func main() {
loop:
	for {
		fmt.Println("Please select an option")
		fmt.Println("1) Print menu")
		fmt.Println("2) Add item")
		fmt.Println("q) quit")
		choice, _ := in.ReadString('\n')

		switch strings.TrimSpace(choice) {
		case "1":
			menu.Print()
		case "2":
			err := menu.Add()
			if err != nil {
				fmt.Println(fmt.Errorf("invalid input: %w", err))
			}
		case "q":
			break loop
		default:
			fmt.Println("Unknown option")
		}
	}
}
```

**Explanation:**
- This code presents a simple menu-driven interface to interact with the menu package.
- It prompts the user to select an option: print the menu, add an item, or quit.
- Based on the user's input, it calls corresponding functions from the `menu` package to perform the desired action.

### `menu` Package

```go
package menu

import (
	"bufio"
	"errors"
	"fmt"
	"os"
	"strings"
)

type menuItem struct {
	name   string
	prices map[string]float64
}

type menu []menuItem

var in = bufio.NewReader(os.Stdin)

func (m menu) print() {
	for _, item := range m {
		fmt.Println(item.name)
		fmt.Println(strings.Repeat("-", 10))
		for size, cost := range item.prices {
			fmt.Printf("\t%10s%10.2f\n", size, cost)
		}
	}
}

func (m *menu) add() error {
	fmt.Println("Please enter the name of the new item")
	name, _ := in.ReadString('\n')
	name = strings.TrimSpace(name)

	for _, item := range data {
		if item.name == name {
			return errors.New("menu item already exists")
		}
	}
	*m = append(*m, menuItem{name: name, prices: make(map[string]float64)})
	return nil
}

func Print() {
	data.print()
}
func Add() error {
	return data.add()
}
```

**Explanation:**
- This code defines the `menu` package, which contains methods to print the menu and add new items to the menu.
- It defines a `menuItem` struct to represent each menu item, which includes the name of the item and a map of prices for different sizes.
- The `print` method prints the menu along with its prices.
- The `add` method allows adding a new item to the menu.
- The `Print` and `Add` functions are exported and serve as entry points for interacting with the menu package from the `main` package.

### `data` Package

```go
package menu

var data = menu{
	{name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
	{name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
}
```

**Explanation:**
- This code initializes the `data` variable with some initial menu items.
- It provides sample data for demonstration purposes.

Now, let's provide the outputs.

### Output

When you run the `main` package, it will present a menu like this:

```
Please select an option
1) Print menu
2) Add item
q) quit
```

If you choose to print the menu (`1`), it will display the menu items along with their prices. If you choose to add an item (`2`), it will prompt you to enter the name of the new item and then add it to the menu. If you choose to quit (`q`), it will exit the program.


# if Statements

```go
package main

import (
	"fmt"
)

func main() {
    // Defining a variable i with value 5 in a short declaration within the if statement
	if i := 5; i < 5 { // Check if i is less than 5
		fmt.Println("i is less than 5")
	} else if i < 10 { // If i is not less than 5, check if i is less than 10
		fmt.Println("i is less than 10")
	} else { // If i is not less than 5 and not less than 10, then it must be greater than or equal to 10





		fmt.Println("i is greater than or equal to 10")
	}
}
```
Output:
```
i is less than 10
```

In this output, the program prints "i is less than 10" because the value of `i` is 5, which satisfies the condition `i < 10`.

Explanation:
- In this Go program, we're using conditional statements (`if`, `else if`, `else`) to check the value of the variable `i`.
- We're also using a short declaration syntax (`:=`) to declare and initialize `i` with a value of 5 within the `if` statement.
- The first `if` statement checks if `i` is less than 5. If it is, it prints "i is less than 5".
- If `i` is not less than 5, the program proceeds to the `else if` statement, which checks if `i` is less than 10. If it is, it prints "i is less than 10".
- If `i` is neither less than 5 nor less than 10, the program goes to the `else` block and prints "i is greater than or equal to 10".

# Panic and Recover

```go
package main

import "fmt"

func main() {
    dividend, divisor := 10, 5
    fmt.Printf("%v divided by %v is %v\n", dividend, divisor, divide(dividend, divisor))

    dividend, divisor = 10, 0
    fmt.Printf("%v divided by %v is %v\n", dividend, divisor, divide(dividend, divisor))
}

func divide(dividend, divisor int) int {
    return dividend / divisor
}
```

Output:
```
10 divided by 5 is 2
panic: runtime error: integer divide by zero
```

Explanation:
- In the first part of the code, we have a `divide` function that performs integer division of two numbers (`dividend` by `divisor`). It doesn't handle the case when the divisor is 0.
- In the `main` function, we call `divide` twice: first with `dividend=10` and `divisor=5`, and then with `dividend=10` and `divisor=0`.
- The first call to `divide` completes successfully, printing "10 divided by 5 is 2".
- However, the second call to `divide` results in a runtime error because we're trying to divide by zero. This error causes the program to panic, which means it abruptly terminates with an error message.

Now, let's modify the program to handle the panic using `recover`:

```go
package main

import "fmt"

func main() {
    dividend, divisor := 10, 5
    fmt.Printf("%v divided by %v is %v\n", dividend, divisor, divide(dividend, divisor))

    dividend, divisor = 10, 0
    fmt.Printf("%v divided by %v is %v\n", dividend, divisor, divide(dividend, divisor))
}

func divide(dividend, divisor int) int {
    defer func() {
        if recover() != nil {
            fmt.Println("Panic detected!")
        }
    }()
    return dividend / divisor
}
```

Output:
```
10 divided by 5 is 2
Panic detected!
0 divided by 0 is 0
```

Explanation:
- In this modified version, we use the `defer` statement to set up a function call (`recover`) to be executed when the `divide` function exits.
- Inside the `defer` function, we check if `recover()` returns a non-nil value. If it does, it means a panic occurred, and we print "Panic detected!".
- Now, when the program encounters the division by zero error, it panics as before. However, this time the panic is caught by the `recover` function inside the `divide` function, preventing the program from terminating abruptly. Instead, it prints "Panic detected!" and continues executing the rest of the code.
- As a result, the program continues to execute, printing "0 divided by 0 is 0" after handling the panic.





# Functions

**Before:**

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

type menuItem struct {
	name   string
	prices map[string]float64
}

var menu = []menuItem{
	{name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
	{name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
}

var in = bufio.NewReader(os.Stdin)

func main() {

loop:
	for {
		fmt.Println("Please select an option")
		fmt.Println("1) Print menu")
		fmt.Println("2) Add item")
		fmt.Println("q) quit")
		choice, _ := in.ReadString('\n')

		switch strings.TrimSpace(choice) {
		case "1":
			for _, item := range menu {
				fmt.Println(item.name)
				fmt.Println(strings.Repeat("-", 10))
				for size, cost := range item.prices {
					fmt.Printf("\t%10s%10.2f\n", size, cost)
				}
			}
		case "2":
			fmt.Println("Please enter the name of the new item")
			name, _ := in.ReadString('\n')
			menu = append(menu, menuItem{name: strings.TrimSpace(name), prices: make(map[string]float64)})
		case "q":
			break loop
		default:
			fmt.Println("Unknown option")
		}
	}

}
```

**Output:**
```
Please select an option
1) Print menu
2) Add item
q) quit
1
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
Please select an option
1) Print menu
2) Add item
q) quit
2
Please enter the name of the new item
Mocha
Please select an option
1) Print menu
2) Add item
q) quit
q
```

**Explanation:**
- The program defines a `menuItem` struct representing items on the menu, which includes a name and a map of sizes to prices.
- It initializes a slice `menu` containing some pre-defined items.
- It uses a loop to continuously prompt the user for options until they choose to quit (`q`).
- Within the loop, it presents options to print the menu (`1`), add a new item (`2`), or quit.
- Depending on the user's choice, it either prints the menu with prices, prompts for a new item's name and adds it to the menu, or quits the program.
- The printing of the menu is done directly inside the `main` function.

**After:**

```go
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

type menuItem struct {
	name   string
	prices map[string]float64
}

var menu = []menuItem{
	{name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
	{name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
}

var in = bufio.NewReader(os.Stdin)

func main() {

loop:
	for {
		fmt.Println("Please select an option")
		fmt.Println("1) Print menu")
		fmt.Println("2) Add item")
		fmt.Println("q) quit")
		choice, _ := in.ReadString('\n')

		switch strings.TrimSpace(choice) {
		case "1":
			printMenu()
		case "2":
			addItem()
		case "q":
			break loop
		default:
			fmt.Println("Unknown option")
		}
	}
}

func printMenu() {
	for _, item := range menu {
		fmt.Println(item.name)
		fmt.Println(strings.Repeat("-", 10))
		for size, cost := range item.prices {
			fmt.Printf("\t%10s%10.2f\n", size, cost)
		}
	}
}
func addItem() {
	fmt.Println("Please enter the name of the new item")
	name, _ := in.ReadString('\n')
	menu = append(menu, menuItem{name: strings.TrimSpace(name), prices: make(map[string]float64)})
}
```

**Output:**
```
Please select an option
1) Print menu
2) Add item
q) quit
1
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
Please select an option
1) Print menu
2) Add item
q) quit
2
Please enter the name of the new item
Mocha
Please select an option
1) Print menu
2) Add item
q) quit
q
```

**Explanation:**
- The code has been refactored to separate concerns by moving the functionality for printing the menu and adding an item into their respective functions `printMenu()` and `addItem()`.
- This makes the code more modular and easier to understand, as each function now has a single responsibility.
- The `main()` function now simply presents options to the user and calls the appropriate function based on their choice.
- The `printMenu()` function is responsible for printing the menu with prices.
- The `addItem()` function prompts the user for a new item's name and adds it to the menu.


---




### `main.go`

```go
package main

import (
    "bufio"
    "demo/menu"
    "fmt"
    "os"
    "strings"
)

var in = bufio.NewRead# Methods er(os.Stdin)

func main() {
    loop:
    for {
        fmt.Println("Please select an option")
        fmt.Println("1) Print menu")
        fmt.Println("2) Add item")
        fmt.Println("q) quit")
        choice, _ := in.ReadString('\n')

        switch strings.TrimSpace(choice) {
        case "1":
            menu.Print()
        case "2":
            err := menu.Add()
            if err != nil {
                fmt.Println(fmt.Errorf("invalid input: %w", err))
            }
        case "q":
            break loop
        default:
            fmt.Println("Unknown option")
        }
    }
}
```

**Explanation:**
- This file contains the main program.
- It provides a menu to the user with options to print the menu, add an item, or quit the program.
- It reads user input and calls the appropriate functions from the `menu` package based on the input.

---

### `menu.go`

```go
package menu

import (
    "bufio"
    "errors"
    "fmt"
    "os"
    "strings"
)

type menuItem struct {
    name   string
    prices map[string]float64
}

var in = bufio.NewReader(os.Stdin)

var menu = []menuItem{
    {name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
    {name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
}

func Print() {
    for _, item := range menu {
        fmt.Println(item.name)
        fmt.Println(strings.Repeat("-", 10))
        for size, cost := range item.prices {
            fmt.Printf("\t%10s%10.2f\n", size, cost)
        }
    }
}

func Add() error {
    fmt.Println("Please enter the name of the new item")
    name, _ := in.ReadString('\n')
    name = strings.TrimSpace(name)

    for _, item := range menu {
        if item.name == name {
            return errors.New("menu item already exists")
        }
    }
    menu = append(menu, menuItem{name: name, prices: make(map[string]float64)})
    return nil
}
```

**Explanation:**
- This file defines the `menu` package.
- It declares a `menuItem` struct to represent menu items.
- It declares a `menu` slice containing sample menu items with their respective prices.
- It provides functions to print the menu (`Print`) and add a new item to the menu (`Add`).

---

### `data.go`

```go
package menu

var menu = []menuItem{
    {name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
    {name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
}
```

**Explanation:**
- This file declares the initial data for the menu.
- It's included here to demonstrate how data can be separated into its own file for organization.

### Output

When you run the `main.go` program, it will display a menu with options to print the menu, add an item, or quit. Here's an example of the output:

```
Please select an option
1) Print menu
2) Add item
q) quit
```

Depending on the user's input, it will either print the menu, prompt the user to add a new item to the menu, or quit the program. The output will vary based on the user's choices.

---

# Methods
### `main` Package

```go
package main

import (
	"bufio"
	"demo/menu"
	"fmt"
	"os"
	"strings"
)

var in = bufio.NewReader(os.Stdin)

func main() {
loop:
	for {
		fmt.Println("Please select an option")
		fmt.Println("1) Print menu")
		fmt.Println("2) Add item")
		fmt.Println("q) quit")
		choice, _ := in.ReadString('\n')

		switch strings.TrimSpace(choice) {
		case "1":
			menu.Print()
		case "2":
			err := menu.Add()
			if err != nil {
				fmt.Println(fmt.Errorf("invalid input: %w", err))
			}
		case "q":
			break loop
		default:
			fmt.Println("Unknown option")
		}
	}
}
```

**Explanation:**
- This code presents a simple menu-driven interface to interact with the menu package.
- It prompts the user to select an option: print the menu, add an item, or quit.
- Based on the user's input, it calls corresponding functions from the `menu` package to perform the desired action.

---

### `menu` Package

```go
package menu

import (
	"bufio"
	"errors"
	"fmt"
	"os"
	"strings"
)

type menuItem struct {
	name   string
	prices map[string]float64
}

type menu []menuItem

var in = bufio.NewReader(os.Stdin)

func (m menu) print() {
	for _, item := range m {
		fmt.Println(item.name)
		fmt.Println(strings.Repeat("-", 10))
		for size, cost := range item.prices {
			fmt.Printf("\t%10s%10.2f\n", size, cost)
		}
	}
}

func (m *menu) add() error {
	fmt.Println("Please enter the name of the new item")
	name, _ := in.ReadString('\n')
	name = strings.TrimSpace(name)

	for _, item := range data {
		if item.name == name {
			return errors.New("menu item already exists")
		}
	}
	*m = append(*m, menuItem{name: name, prices: make(map[string]float64)})
	return nil
}

func Print() {
	data.print()
}
func Add() error {
	return data.add()
}
```

**Explanation:**
- This code defines the `menu` package, which contains methods to print the menu and add new items to the menu.
- It defines a `menuItem` struct to represent each menu item, which includes the name of the item and a map of prices for different sizes.
- The `print` method prints the menu along with its prices.
- The `add` method allows adding a new item to the menu.
- The `Print` and `Add` functions are exported and serve as entry points for interacting with the menu package from the `main` package.

---

### `data` Package

```go
package menu

var data = menu{
	{name: "Coffee", prices: map[string]float64{"small": 1.65, "medium": 1.80, "large": 1.95}},
	{name: "Espresso", prices: map[string]float64{"single": 1.90, "double": 2.25, "triple": 2.55}},
}
```

**Explanation:**
- This code initializes the `data` variable with some initial menu items.
- It provides sample data for demonstration purposes.

Now, let's provide the outputs.

### Output

When you run the `main` package, it will present a menu like this:

```
Please select an option
1) Print menu
2) Add item
q) quit
```

If you choose to print the menu (`1`), it will display the menu items along with their prices. If you choose to add an item (`2`), it will prompt you to enter the name of the new item and then add it to the menu. If you choose to quit (`q`), it will exit the program.


---


# Object Orientation and Polymorphism

**Methods:**

In Go, methods are functions associated with a particular type. They allow you to associate behavior with data structures. Methods are defined using the `func` keyword followed by the receiver type. The receiver type is the type upon which the method operates.

```go
package main

import "fmt"

type Rectangle struct {
    length, width float64
}

// Method to calculate the area of Rectangle
func (r Rectangle) Area() float64 {
    return r.length * r.width
}

func main() {
    rect := Rectangle{length: 5, width: 3}
    fmt.Println("Area of Rectangle:", rect.Area())
}
```

**Output:**

```go
Area of Rectangle: 15
```

---

**Interfaces:**

Interfaces in Go provide a way to specify behavior without actually implementing it. An interface is a set of method signatures. Any type that implements all the methods of an interface implicitly implements that interface.

```go
package main

import "fmt"

type Shape interface {
    Area() float64
}

type Rectangle struct {
    length, width float64
}

// Implementing the Area method for Rectangle
func (r Rectangle) Area() float64 {
    return r.length * r.width
}

func PrintArea(s Shape) {
    fmt.Println("Area:", s.Area())
}

func main() {
    rect := Rectangle{length: 5, width: 3}
    PrintArea(rect)
}
```

**Output:**

```go
Area: 15
```

---

**Basic Generics:**

Generics allow you to write functions and data structures that can work with any type. In Go 1.18 and later versions, basic generics are introduced, enabling you to write generic code using type parameters.

```go
package main

import "fmt"

func PrintSlice[T any](s []T) {
    for _, v := range s {
        fmt.Println(v)
    }
}

func main() {
    ints := []int{1, 2, 3}
    PrintSlice(ints)

    strings := []string{"apple", "banana", "orange"}
    PrintSlice(strings)
}
```

**Output:**

```go
1
2
3
apple
banana
orange
```

---

**Generic Constraints:**

Generic constraints allow you to restrict the types that can be used with a generic function or data structure. You can specify constraints using interface types or predefined type sets.

```go
package main

import "fmt"

type Adder[T any] interface {
    Add(T, T) T
}

func Sum[T Adder[T]](a, b T) T {
    return a.Add(a, b)
}

type Int int

func (i Int) Add(a, b Int) Int {
    return a + b
}

func main() {
    result := Sum(Int(3), Int(5))
    fmt.Println("Sum:", result)
}
```

**Output:**

```go
Sum: 8
```

---

**Type Interfaces:**

In Go, interfaces can be implemented implicitly. This means that any type that implements the methods of an interface without explicitly declaring it satisfies that interface.

```go
package main

import "fmt"

type Printable interface {
    Print()
}

type Person struct {
    Name string
}

// Implementing Printable interface
func (p Person) Print() {
    fmt.Println("Name:", p.Name)
}

func main() {
    var p Printable = Person{Name: "Saklain"}
    p.Print()
}
```

**Output:**

```go
Name: Saklain
```

---

# Error Management

**1. Creating Errors:**
In Go, errors are represented by the `error` interface, which is defined as:
```go
type error interface {
    Error() string
}
```
To create a new error, you can use the `errors` package:
```go
package main

import (
    "errors"
    "fmt"
)

func main() {
    err := errors.New("This is an example error")
    fmt.Println(err.Error())
}
```
**Output:**
```
This is an example error
```

---

**2. Comma Error Pattern:**
The comma error pattern in Go is a common idiom used to handle errors. It involves using the comma-ok syntax in conjunction with if statements to check for errors and handle them gracefully.
```go
package main

import (
    "fmt"
)

func divide(a, b int) (int, error) {
    if b == 0 {
        return 0, fmt.Errorf("cannot divide by zero")
    }
    return a / b, nil
}

func main() {
    result, err := divide(10, 2)
    if err != nil {
        fmt.Println("Error:", err)
        return
    }
    fmt.Println("Result:", result)
}
```
**Output:**
```
Result: 5
```

---

**3. Panic vs. Error:**
In Go, `panic` and `error` are two mechanisms for handling exceptional situations, but they serve different purposes.
- **Panic:** It is used to terminate the program abruptly when something unexpected happens, such as a runtime error. Panics are generally not used for routine error handling.
- **Error:** Errors are used to indicate expected and recoverable problems in the program flow. They are propagated up the call stack until they are handled.

**Sample Program demonstrating Panic and Error:**
```go
package main

import "fmt"

func main() {
    defer func() {
        if r := recover(); r != nil {
            fmt.Println("Recovered from panic:", r)
        }
    }()
    panicExample()
    fmt.Println("This line will not be executed due to panic.")
}

func panicExample() {
    panic("This is a panic example")
}
```
**Output:**
```
Recovered from panic: This is a panic example
```



# Goroutines and WaitGroups

Goroutines are lightweight threads managed by the Go runtime. They allow functions to be executed concurrently. WaitGroups are used to wait for a collection of goroutines to finish executing before continuing.



```go
package main

import (
	"fmt"
	"sync"
	"time"
)

func worker(id int, wg *sync.WaitGroup) {
	defer wg.Done() // Decrements the WaitGroup counter when the function exits
	fmt.Printf("Worker %d starting\n", id)
	time.Sleep(time.Second) // Simulate some work
	fmt.Printf("Worker %d done\n", id)
}

func main() {
	var wg sync.WaitGroup

	for i := 1; i <= 3; i++ {
		wg.Add(1) // Increment the WaitGroup counter for each goroutine
		go worker(i, &wg)
	}

	wg.Wait() // Blocks until the WaitGroup counter becomes zero
	fmt.Println("All workers done")
}
```

### Output:

```
Worker 1 starting
Worker 2 starting
Worker 3 starting
Worker 2 done
Worker 1 done
Worker 3 done
All workers done
```

# Channels

Channels are the pipes that connect concurrent goroutines. You can send values into channels from one goroutine and receive those values into another goroutine.



```go
package main

import "fmt"

func sendMessages(messages chan string) {
	messages <- "Hello"
	messages <- "World"
	close(messages)
}

func main() {
	messages := make(chan string)

	go sendMessages(messages)

	for msg := range messages {
		fmt.Println(msg)
	}
}
```

### Output:

```
Hello
World
```

# Select Statements

The `select` statement lets a goroutine wait on multiple communication operations. It blocks until one of its cases can proceed, then it executes that case.


```go
package main

import (
	"fmt"
	"time"
)

func main() {
	ch1 := make(chan string)
	ch2 := make(chan string)

	go func() {
		time.Sleep(1 * time.Second)
		ch1 <- "one"
	}()

	go func() {
		time.Sleep(2 * time.Second)
		ch2 <- "two"
	}()

	for i := 0; i < 2; i++ {
		select {
		case msg1 := <-ch1:
			fmt.Println("Received", msg1)
		case msg2 := <-ch2:
			fmt.Println("Received", msg2)
		}
	}
}
```

### Output:

```
Received one
Received two
```

# Ranging Over Channels

You can range over channels to iterate over the values received from the channel until it is closed.


```go
package main

import "fmt"

func produce(ch chan int) {
	for i := 0; i < 5; i++ {
		ch <- i
	}
	close(ch)
}

func main() {
	ch := make(chan int)

	go produce(ch)

	for num := range ch {
		fmt.Println("Received", num)
	}
}
```

### Output:

```
Received 0
Received 1
Received 2
Received 3
Received 4
```

# Testing in Go

Go has a built-in testing framework that allows you to write and execute tests easily.



```go
package main

import "testing"

func Add(a, b int) int {
	return a + b
}

func TestAdd(t *testing.T) {
	result := Add(2, 3)
	if result != 5 {
		t.Errorf("Add(2, 3) = %d; want 5", result)
	}
}
```

### Running Tests:

To run tests, you can use the `go test` command:

```
go test
```

This will automatically find and run tests in any files named `*_test.go` in the current directory and its subdirectories.
