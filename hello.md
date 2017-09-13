## Workspace
Primeiro precisamos falar sobre o workspace, ou seja a estrutura para trabalharmos com GO. Go precisa ter um **GOPATH**,se não criar um o default será *~/go/*.
Dentro do **GOPATH** criaremos 3 pastas sendo elas:
* **`bin`** => diretório com teus executáveis(compilados).
* **`pkg`** => diretório com os compilados por OS.
* **`src`** => diretório com seus pacotes/projetos e pacotes de terceiros.
Com a estrutura pronta podemos começar a programar =).  

## Hello World
Para não fugirmos do costume, vamos ver um **hello world**, aproveitamos para conhecer a estrutura de uma aplição em GO.

*Crie uma pasta chamada hello dentro do diretório `src`.*
```go
package main

import "fmt"

func main() {
    fmt.Println("Hello World!")
}
```
Para executar este código rodamos o seguinte comando:
> go run main.go

No seguinte comando faremos duas coisas, primeiro vamos compilar o projeto e depois executá-lo:
> go build && ./hello

Nossa primeira aplicação foi criada, agora vamos olhar um pouco sua estrutura.
A primeira linha precisamos definir o package do arquivo, ou seja qual pacote ele pertence. O package main é o principal/inicial da aplicação, ele é importante para que possamos criar nossa aplicação com módulos assim conseguindo ter um código organizado ou mesmo bibliotecas para usar em outras aplicações.  
Segundo tempos a instrução `import` esta é a forma que adicionamos pacotes no nosso projeto, é equivalente ao *include*,*require* de outras aplicações.
Terceira linha temos a `func main()` está é a função inicia nossa aplicação/pacote. *Importante lembrar que só podemos ter uma função  `main  no nosso projeto*.
Por último usamos a função `Println()` do pacote `fmt` para exibirmos nosso *hello World* no console.
___
