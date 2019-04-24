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
![Start Debugging](https://github.com/twodude/go-ethereum/blob/master/docs/images/Screen%20Shot%202019-04-24%20at%204.54.12%20PM.png)

We need to set a "--nodiscover" option on debugging mode. VS Code keeps debugging configuration information in a ```launch.json``` file located in a .vscode folder in your workspace (project root folder) or in your user settings or workspace settings. To create a launch.json file, open your project folder in VS Code (File > Open Folder) and then select the Configure gear icon on the Debug view top bar.

Change the ```args``` with the following code:

```json
"args": [
    "--nodiscover"
]
```
