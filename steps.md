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