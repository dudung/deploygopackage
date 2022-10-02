# deploygopackage
learn to deploy a go package


## 02-oct-2022
+ [Some steps](steps.md) I tried but not works.
+ Get message while creating package.
```shell
PS L:\home\deploygopackage> go mod tidy
github.com/dudung/deploygopackage: reading L:\home\deploygopackage\deploygopackage.go: unexpected NUL in input
```
+ Get message while installing package.
```shell
PS L:\home\deploygopackage\test> go mod tidy
go: finding module for package github.com/dudung/deploygopackage
go: found github.com/dudung/deploygopackage in github.com/dudung/deploygopackage v0.0.1
test/atest imports
        github.com/dudung/deploygopackage: reading C:\Users\Sparisoma Viridi\go\pkg\mod\github.com\dudung\deploygopackage@v0.0.1\deploygopackage.go: unexpected NUL in input
```
+ It does not work.
```shell
PS L:\home\deploygopackage\test> go run .
index.go:5:3: no required module provides package github.com/dudung/deploygopackage; to add it:
        go get github.com/dudung/deploygopackage
```
+ Event the files are installed.
```shell
  PS L:\home\deploygopackage> ls "C:\Users\Sparisoma Viridi\go\pkg\mod\github.com\dudung\deploygopackage@v0.0.1"
    
      Directory: C:\Users\Sparisoma Viridi\go\pkg\mod\github.com\dudung\deploygopackage@v0.0.1
    
  Mode                 LastWriteTime         Length Name
  ----                 -------------         ------ ----
  -ar---        2022-10-02     12:18            269 .gitignore
  -ar---        2022-10-02     12:18           2572 deploygopackage.go
  -ar---        2022-10-02     12:18             50 go.mod
  -ar---        2022-10-02     12:18           1073 LICENSE
  -ar---        2022-10-02     12:18             47 README.md
  -ar---        2022-10-02     12:18           3467 steps.md
```
+ Contact Chaudhary with following message.
  
  > Should we first clone the GitHub repository or `git init` before we can use `git add .`? I am following your instructions, perhaps I miss something, and get the message `fatal: not a git repository (or any of the parent directories): .git`. Any clue would be very helpful. Thank you.

## refs
+ Shreya Chaudhary, "Creating and Deploying your First Go Package", Towards Data Science, 22 May 2022, url <https://towardsdatascience.com/eae220905745> [20221002].