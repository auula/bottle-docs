### Install Module🚀

You just need to install the Bottle module in your project to use:

```shell
go get -u github.com/auula/bottle
```

### Bottle Source code🌲

```shell
.
├── LICENSE
├── README.md
├── bottle-logo.svg
├── bottle.go           # Main File
├── bottle_test.go      
├── encoding.go         # Data encoding module
├── encrypted.go        # Data encrypted module
├── encrypted_test.go
├── example             # Exmaple code
│   ├── config.yaml
│   ├── demo_exchange.go
│   └── demo_put_get.go
├── go.mod
├── go.sum
├── gopher-bottle.svg
├── hashed.go          # Hashed function
├── item.go            # Data log Entry
└── option.go          # Bottle Configure 

1 directory, 17 files

```

### Data Directory 📑

Since the bottle design is based on a single-process program, each storage instance corresponds to a `data` directory, `data` is the log merge structure data directory, and `index` is the `index` data version.

Log consolving structural data The current version is merged every time the data is started. The default is that all data files under the DATA data folder occupies the total and more than `1GB` of more than `1GB` will trigger a merge, and the data that is not used after the merger is discarded.

Of course, if the dirty data merge requirements are not reached, the data file is archived in the size of the configured, each data has a version number, and is set to read-only mount, the process work directory structure is as follows:

```shell
./testdata
├── data
│   └── 1.data
└── index
    ├── 1646378326.index
    └── 1646378328.index

2 directories, 3 files
```
When the storage engine starts working, the folder and files can only be operated by this process to ensure data security.