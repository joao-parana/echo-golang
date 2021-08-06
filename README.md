# echo-golang

```bash
go run main.go Este é um teste
go build main.go
copy main.exe C:\Windows\echo-golang.exe # use administrative prvileges bash shell
```

Exemplo de progrma golang para manipular o environment

```go
cat main.go
package main

import (
  "bytes"
  "fmt"
  "os"
  "log"
  // Import godotenv
  "github.com/joho/godotenv"
)

// use godot package to load/read the .env file and
// return the value of the key
func goDotEnvVariable(key string) string {

  // load .env file
  err := godotenv.Load(".env")

  if err != nil {
    // log.Fatalf("Error loading .env file")
    fmt.Printf("Error loading .env file")
  }

  return os.Getenv(key)
}

// use os package to get the env variable which is already set
func getEnvVariable(key string) string {

  // set env variable using os package
  // os.Setenv(key, "gopher")

  // return the env variable using os package
  return os.Getenv(key)
}

func main() {
  var (
    buf    bytes.Buffer
    logger = log.New(&buf, "logger: ", log.Lshortfile)
  )

  logger.Print("Hello, log file!")

  fmt.Print(&buf)

  // os package
  value := getEnvVariable("Path")

  fmt.Printf("os package: %s = %s \n", "name", value)

  // godotenv package
  dotenv := goDotEnvVariable("STRONGEST_AVENGER")

  fmt.Printf("godotenv : %s = %s \n", "STRONGEST_AVENGER", dotenv)
}
```


