## Building Geth and Debugging with VS Code

### Install Golang
TBA

### Get Geth
Get go-ethereum from a github repository. You can find it at "$GOPATH/src" like "/⁨Users⁩/⁨luke⁩/⁨go/⁨src/⁨github.com/⁨ethereum⁩".
```bash
$ go get -d github.com/ethereum/go-ethereum
```

### Build Geth
Add "$GOPATH/bin" to $PATH first.
```bash
$ go install github.com/ethereum/go-ethereum/cmd/geth
$ ls -al </Users/luke/go/bin> | grep geth
-rwxr-xr-x  1 luke  staff  44706256 Apr 24 16:11 geth
```

### Run Geth without Sync.
```bash
$ geth --nodiscover
```
Input 'Ctrl + C' to exit.

You must rebuild geth after changing the code. For example, add the following code in 284th line in ```cmd/geth/main.go```:
```go
fmt.Println("Hello, world!")
```
Then
```bash
$ go install -v github.com/ethereum/go-ethereum/cmd/geth
github.com/ethereum/go-ethereum/cmd/geth
$ geth --nodiscover
Hello, world!
...
```

### Debugging with VS Code
```bash
go get -u github.com/derekparker/delve/cmd/dlv
```
Restart VS Code. Now you can start debugging:
