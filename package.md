## Packages

	Combina biblioteca,namespace e módulo em numa única declaração.  

Go tem uma tool para fazer download e instalação de packages, ela se chama **get**. A sintaxe para baixar um pacote é a seguinte: *O parâmetro -u é usado para baixar as dependências e atualizar o pacote*   

> go get -u github.com/golang/dep/cmd/dep
Acessando *cd $GOPATH/src* deverá ver uma pasta github/golang/dep. Está é a forma como go trabalha com o armazenamento de pacotes.  

###  Importar pacotes no projeto
	O último nome do import path é o pacote. 

Go possui a palavra reservada *import*, para funções da *standard library* apenas colocamos o nome do pacote, por ex.:
```go
import "fmt"
import(
	"math"
	"log"
)
```
Podemos usar álias para chamarmos nosso pacote, por ex."
```go
import f "fmt"
f.Println("Isso deverá funcionar")
```

Pacotes podem ter "subpacotes", um exemplo é o pacote *encoding*. Quando precisarem usar funções para trabalhar com JSON, usarão *encoding/json*. Que nada mais é do que um pacote dentro do pacote encoding.
```go
import "encoding/json"
```

### Agora vamos falar sobre os nossos pacotes
	Todos arquivos devem conter o mesmo package name.  

Como já devem ter notado o formato dos pacotes é repositório/user/package. Seguindo esta regra vamos criar nosso pacote. 
Mesmo quando vamos criar um pacote interno devemos seguir esta estrutura, quando importarmos não devemos fazer algo como **import ./meuPacote**.

```go
// $GOPATH/src/github.com/renatosuero/unuseful
package unuseful
func Something(){
}
```

GO tem uma regra para proteger funções, ou seja, funções que você usa internamente no seu pacote. Para este caso você precisa definir sua função com a primeira letra minúscula.  

```go
package unuseful
func Something(){
	secretFunc()
}
func secretFunc(){
}
```

Também é possível criar pacotes dentro de pacotes. Vamos criar um novo pacote dentro do nosso pacote *unusefull*.
Criamos uma pasta chamada foo e digitamos o seguinte código: *O caso do pacote encoding/json que vimos antes*
```go
package foo
func Bar(){
}
```

Pode haver situações onde vc quer só carregar o pacote e não usar funções dele. Por ex. pacotes de drivers para databases. Estas funções serão carregadas no ínicio da execução do projeto, podemos usar estas funções para inicializar nossa lógica. Para isso criamos a função **init**.
```go
package unuseful
import "fmt"
func init(){
	fmt.Println("Carregou nosso pacote")
}
```
Nestes casos onde você apenas quer carregar o **init** e não chama nenhuma função, o compilador irá mostrar um erro. Para resolvermos isso adicionamos um **_** antes do pacote.
```go
import _ "unuseful
```
---

