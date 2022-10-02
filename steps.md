## create a new repository
1. Login to a GitHub account through <https://github.com/login>.
2. Create a new repository using + icon or <https://github.com/new>.
3. Fill Repository name, e.g. deploygopackage.
4. Type Description, e.g. learn to deploy a go package.
5. Select Public.
6. Check Add a README file, if necessary.
7. Add .gitignore by choosing Go.
8. Choose a license, e.g. MIT License.
9. Click Create repository button.
10. Visit the repository, e.g. <https://github.com/dudung/deploygopackage>,


## clone remote repository to local directory
1. Clone remote repository.
  ```
  PS L:\home> git clone https://github.com/dudung/deploygopackage
  Cloning into 'deploygopackage'...
  remote: Enumerating objects: 5, done.
  remote: Counting objects: 100% (5/5), done.
  remote: Compressing objects: 100% (4/4), done.
  remote: Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
  Receiving objects: 100% (5/5), done.
  ```
2. Change diretory.
  ```shell
  PS L:\home> cd deploygopackage
  ```
3. List the files.
  ```shell
    PS L:\home\deploygopackage> ls
    
      Directory: L:\home\deploygopackage
    
    Mode                 LastWriteTime         Length Name
    ----                 -------------         ------ ----
    -a----        2022-10-02     08:15            284 .gitignore
    -a----        2022-10-02     08:15           1094 LICENSE
    -a----        2022-10-02     08:15             49 README.md
  ```


## make go module
1. Make a Go module.
  ```shell
  PS L:\home\deploygopackage> go mod init github.com/dudung/deploygopackage
  go: creating new go.mod: module github.com/dudung/deploygopackage
  ```
2. Create a Go file with first line is package deploygopackage.
  ```shell
  PS L:\home\deploygopackage> echo "package deploygopackage" > deploygopackage.go
  ```
3. Edit the file and type following lines.
  ```go
  import (
      "fmt"
      "log"
      "os"
  )

  func write_index_html() {
    fname := "/static/index.html"
    dest, err := os.Create(fname)
    if err != nil {
      fmt.Println("os.Create:", err)
      return
    }
    defer dest.Close()
    
    fmt.Fprintf(dest, "<!doctype html>\n")
    fmt.Fprintf(dest, "<html lang='en'>\n")
    fmt.Fprintf(dest, "  <head>\n")
    fmt.Fprintf(dest, "    <title>Hello Wordl</title>\n")
    fmt.Fprintf(dest, "    <link rel='stylesheet' href='style.css' />\n")
    fmt.Fprintf(dest, "  </head>\n")
    fmt.Fprintf(dest, "  <body>\n")
    fmt.Fprintf(dest, "    <h1>Hello, Wordl!</h1>\n")
    fmt.Fprintf(dest, "    <p>Sat, 1 Oct 2022</p>\n")
    fmt.Fprintf(dest, "  </body>\n")
    fmt.Fprintf(dest, "</html>\n")
  }

  func write_style_css() {
    fname := "/static/style.css"
    dest, err := os.Create(fname)
    if err != nil {
      fmt.Println("os.Create:", err)
      return
    }
    defer dest.Close()
    
    fmt.Fprintf(dest, "h1 {\n")
    fmt.Fprintf(dest, "  color: blue;\n")
    fmt.Fprintf(dest, "}\n")
  }

  func delete_index_html() {
    e := os.Remove("/static/index.html")
    if e != nil {
        log.Fatal(e)
    }
  }

  func delete_style_css() {
    e := os.Remove("/static/style.css")
    if e != nil {
        log.Fatal(e)
    }
  }
  ```
6. Save it.
7. Update necessary modules, but not work.
  ```shell
  PS L:\home\deploygopackage> go mod tidy
  github.com/dudung/deploygopackage: reading L:\home\deploygopackage\deploygopackage.go: unexpected NUL in input
  ```


## connect to github and commit the code
1. Add files and commit changes.
  ```shell
  /l/home/deploygopackage (main)
  $ git add deploygopackage.go go.mod steps.md
  warning: LF will be replaced by CRLF in go.mod.
  The file will have its original line endings in your working directory
  ```
2. Commit changes.
  ```shell
   /l/home/deploygopackage (main)
  $ git commit -a -m "create first commit of a go package"
  [main 3f2d799] create first commit of a go package
   3 files changed, 123 insertions(+)
   create mode 100644 deploygopackage.go
   create mode 100644 go.mod
   create mode 100644 steps.md
  ```
3. Push commit to repository.
  ```shell
  /l/home/deploygopackage (main)
  $ git push
  Enumerating objects: 6, done.
  Counting objects: 100% (6/6), done.
  Delta compression using up to 4 threads
  Compressing objects: 100% (5/5), done.
  Writing objects: 100% (5/5), 2.14 KiB | 730.00 KiB/s, done.
  Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
  To https://github.com/dudung/deploygopackage
     7360240..3f2d799  main -> main
  ```
4. Create tag.
  ```shell
  /l/home/deploygopackage (main)
  $ git tag v0.0.1
  ```
5. Push tag to repository.
  ```shell
  /l/home/deploygopackage (main)
  $ git push origin v0.0.1
  Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
  To https://github.com/dudung/deploygopackage
   * [new tag]         v0.0.1 -> v0.0.1
  ```

## create test project
1. Make directory and change it.
  ```shell
  /l/home/deploygopackage (main)
  $ mkdir test && cd test
  ```
2. Make test project.
  ```shell
  /l/home/deploygopackage/test (main)
  $ touch index.go
  ```
3. Edit the file and type following lines
  ```go
  package main

  import (
    "fmt"
    "github.com/dudung/deploygopackage"
  )

  func main() {
    deploygopackage.write_index_html()
    deploygopackage.write_style_css()
  }
  ```
4. Save it.
5. Update necessary modules.
  ```shell
  $ go mod tidy
  go: finding module for package github.com/dudung/deploygopackage
  go: found github.com/dudung/deploygopackage in github.com/dudung/deploygopackage v0.0.1
  test/atest imports
          github.com/dudung/deploygopackage: reading C:\Users\Sparisoma Viridi\go\pkg\mod\github.com\dudung\deploygopackage@v0.0.1\deploygopackage.go: unexpected NUL in input
  ```
6. Run the test but not work.
  ```shell
   /l/home/deploygopackage/test (main)
  $ go run .
  index.go:5:3: no required module provides package github.com/dudung/deploygopackage; to add it:
          go get github.com/dudung/deploygopackage
  ```