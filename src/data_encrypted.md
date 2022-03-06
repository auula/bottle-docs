### Encryptor🔐

The data `encryptor` records the value of the data, that is, the block encryption at the field level, instead of encrypting the entire file once, which will cause performance consumption, so the block data segment encryption method is adopted.

The following example uses the [`bottle.SetEncryptor(Encryptor,[]byte)`](https://github.com/auula/bottle/blob/main/option.go#L66) function to set the data encryptor and configure the 16-bit data encryption key.

```go
func init() {
    bottle.SetEncryptor(bottle.AES(), []byte("1234567890123456"))
}
```

You can also customize the interface to implement the data encryptor:

```go
// SourceData for encryption and decryption
type SourceData struct {
    Data   []byte
    Secret []byte
}

// Encryptor used for data encryption and decryption operation
type Encryptor interface {
    Encode(sd *SourceData) error
    Decode(sd *SourceData) error
}
```

The following code is the implementation code of the built-in `AES` encryptor, just implement the [`bottle.Encryptor`](https://github.com/auula/bottle/blob/main/encrypted.go#21) interface, and the data source is the [`bottle.SourceData`](https://github.com/auula/bottle/blob/main/encrypted.go#15) structure field:

```go
// AESEncryptor Implement the Encryptor interface
type AESEncryptor struct{}

// Encode source data encode
func (AESEncryptor) Encode(sd *SourceData) error {
    sd.Data = aesEncrypt(sd.Data, sd.Secret)
    return nil
}

// Decode source data decode
func (AESEncryptor) Decode(sd *SourceData) error {
    sd.Data = aesDecrypt(sd.Data, sd.Secret)
    return nil
}
```
The specific encryptor implementation code can be viewed in [`encrypted.go`](https://github.com/auula/bottle/blob/main/encrypted.go)