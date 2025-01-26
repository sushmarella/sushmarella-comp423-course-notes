
* Primary author: Sushant Marella (https://github.com/sushmarella)
* Reviewer: Aidan Lee (https://github.com/aidanjlee5)

Create a New Go Project

In a terminal (on your **host machine**, not inside a container), create a folder for your Go project. This folder will house your code and Dev Container configurations:

```bash
mkdir hello-go
cd hello-go
```

### Initialize a Git Repository

Initialize a new Git repository inside this folder:

```bash
git init
```

---


### Add a README.md

Create a README file: 

```
echo "COMP423 Go Tutorial: https://sushmarella.github.io/sushmarella-comp423-course-notes/tutorials/go-setup/" > README.md
```
git
## 3. Dev Container Configuration

Inside `hello-go`, create a hidden folder named `.devcontainer` and a file named `devcontainer.json`:

```bash
mkdir .devcontainer
touch .devcontainer/devcontainer.json
```

Open `devcontainer.json` in your editor and add the following content:

```json title=".devcontainer/devcontainer.json"
{
  "name": "Go Dev Container",
  "image": "mcr.microsoft.com/vscode/devcontainers/go:0-1",
  "settings": {
    "terminal.integrated.shell.linux": "/bin/bash"
  },
  "extensions": [
    "golang.Go"
  ]
}
```

### Explanation
- **`name`**: A friendly label for your container.
- **`image`**: Uses a Microsoft-provided Go environment.  
- **`extensions`**: Lists the VS Code extensions you want installed automatically (here, the official Go extension).
- **No host installation needed**: The container has Go built-in, so your local machine only needs Docker, VS Code, and Git.

---

## 4. Reopen in Container

1. **Open** the `hello-go` folder in **VS Code**.
2. If prompted, select **“Reopen in Container”**. Otherwise, open the Command Palette (`Ctrl+Shift+P` or `Cmd+Shift+P`) and select:
   ```
   Dev Containers: Open Folder in Container...
   ```
3. VS Code will build and launch the Dev Container, installing Go and the Go plugin.

!!! tip "Verify Go"
    After the container starts, open a new VS Code terminal and run:
    ```bash
    go version
    ```
    You should see output like `go version go1.xx linux/amd64`, confirming Go is running inside the container.

---

## 5. Initialize Your Go Module

In the container’s terminal, initialize a new Go module for your project:

```bash
go mod init hello-go
```

This creates a `go.mod` file, which tracks your module name (`hello-go`) and any dependencies you add later.

---

## 6. Write a “Hello COMP423” Program

In your `hello-go` folder, create a file named **`main.go`** with the following code:

```go title="main.go"
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423")
}
```

---

## 7. Build and Run Your Go Program

### 7.1 Using `go build`
Compile your program:

```bash
go build
```

- This command creates a binary named `hello-go` in your folder.
- It parallels `gcc main.c -o main` in a C workflow.

Run the binary directly:

```bash
./hello-go
```

You should see:

```
Hello COMP423
```

### 7.2 Using `go run`
Alternatively, compile and run in one step:

```bash
go run .
```

- **`go run .`** compiles and runs on the fly, leaving no binary behind.
- **`go build`** leaves a standalone executable you can run multiple times.


---

## 8. Commit and Push Your Changes

When you’re ready:

```bash
git add .
git commit -m "Initial Go Dev Container setup"
```

Push to GitHub if you have a remote set up:

```bash
git remote add origin <your-repo-url>
git push -u origin main
```

---

## Conclusion
  

With this setup, anyone who clones your repo can open the project in VS Code, run the container, and start coding in Go — **no local Go installation needed**.