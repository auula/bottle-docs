### Configuration Information

You can also use the default configuration, you can initialize your storage engine with the structure of the built-in [`bottle.Option`](https://github.com/auula/bottle/blob/main/option.go#14), and the configuration instance is as follows:

```go
func init() {
    // Custom configuration information
    option := bottle.Option{
        // Working directory
        Directory:       "./data",
        // Algorithm opens encryption
        Enable:          true,
        // Customize the secret, you can use a built-in secret
        Secret:          bottle.Secret,
        // Custom data size, storage unit is KB
        DataFileMaxSize: 1048576,
    }
    // Custom configuration information
    bottle.Open(option)
}
```

Of course, you can also use the built-in [`bottle.Load(path string)`](https://github.com/auula/bottle/blob/main/bottle.go#157)  function to load the configuration file to start Bottle, the configuration file format is `YAML`, the configurable items are as follows:

```go
# Bottle config options
Enable: TRUE
Secret: "1234567890123456"
Directory: "./testdata"
DataFileMaxSize: 536870912
```

It is important to note that the key implemented by the built-in encryptor must be `16` bits, if you are a custom implementation encrypler to set your custom encryprators through [`bottle.SetEncryptor(Encryptor,[]byte)`](https://github.com/auula/bottle/blob/main/option.go#L66), then this secretThe number of digits will not be restricted.