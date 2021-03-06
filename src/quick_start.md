### Install Moduleπ

You just need to install the Bottle module in your project to use:

```shell
go get -u github.com/auula/bottle
```

### Bottle Source codeπ²

```shell
.
βββ LICENSE
βββ README.md
βββ bottle-logo.svg
βββ bottle.go           # Main File
βββ bottle_test.go      
βββ encoding.go         # Data encoding module
βββ encrypted.go        # Data encrypted module
βββ encrypted_test.go
βββ example             # Exmaple code
βΒ Β  βββ config.yaml
βΒ Β  βββ demo_exchange.go
βΒ Β  βββ demo_put_get.go
βββ go.mod
βββ go.sum
βββ gopher-bottle.svg
βββ hashed.go          # Hashed function
βββ item.go            # Data log Entry
βββ option.go          # Bottle Configure 

1 directory, 17 files

```

### Data Directory π

Since the bottle design is based on a single-process program, each storage instance corresponds to a `data` directory, `data` is the log merge structure data directory, and `index` is the `index` data version.

Log consolving structural data The current version is merged every time the data is started. The default is that all data files under the DATA data folder occupies the total and more than `1GB` of more than `1GB` will trigger a merge, and the data that is not used after the merger is discarded.

Of course, if the dirty data merge requirements are not reached, the data file is archived in the size of the configured, each data has a version number, and is set to read-only mount, the process work directory structure is as follows:

```shell
./testdata
βββ data
β   βββ 1.data
βββ index
    βββ 1646378326.index
    βββ 1646378328.index

2 directories, 3 files
```
When the storage engine starts working, the folder and files can only be operated by this process to ensure data security.