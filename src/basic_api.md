### Basic API ⚙

Below is a usage example of a basic data manipulation I wrote:

```go
package main

import (
	"fmt"
	"github.com/auula/bottle"
)

func init() {
	// Open a storage instance by default configuration
	err := bottle.Open(bottle.DefaultOption)
	// And handle possible errors
	if err != nil {
		panic(err)
	}
}

// Userinfo test data structure
type Userinfo struct {
	Name  string
	Age   uint8
	Skill []string
}

func main() {

	// PUT Data
	bottle.Put([]byte("foo"), []byte("66.6"))

	// If it is converted to string, it is a string
	fmt.Println(bottle.Get([]byte("foo")).String())

	// If there is no default, it is 0
	fmt.Println(bottle.Get([]byte("foo")).Int())

	// If it is not success, it is false.
	fmt.Println(bottle.Get([]byte("foo")).Bool())

	// If it is not success, it is 0.0
	fmt.Println(bottle.Get([]byte("foo")).Float())

	user := Userinfo{
		Name:  "Leon Ding",
		Age:   22,
		Skill: []string{"Java", "Go", "Rust"},
	}

	var u Userinfo

	// Save the data object by BSON, and set the timeout for 5 seconds
    // TTL timeout can not set demand
	bottle.Put([]byte("user"), bottle.Bson(&user), bottle.TTL(5))

	// Analysis of structures by unwrap
	bottle.Get([]byte("user")).Unwrap(&u)

	// Print value
	fmt.Println(u)

	// Remove key 'foo'
	bottle.Remove([]byte("foo"))

	// Close handleable error that may happen
	if err := bottle.Close(); err != nil {
		fmt.Println(err)
	}
}
```

The following is a separate variable assignment and catch handling errors:

```go
    data := bottle.Get([]byte("user"))

	if data.IsError() {
		fmt.Println(data.Err)
	} else {
		fmt.Println(data.Value)
	}
```