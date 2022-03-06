### Hashed 🧰

If you need to customize the salad function, you can implement the [bottle.Hashed](https://github.com/auula/bottle/blob/main/hashed.go#10) interface:

```go
type Hashed interface {
    Sum64([]byte) uint64
}
```
Then complete your hash function configuration by built-in [`bottle.SetHashFunc(hash Hashed)`](https://github.com/auula/bottle/blob/main/option.go#85) settings.