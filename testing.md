## Testing
GO tem um pacote muito bacana e simples para escrever nossos testes. Precisamos seguir alguns padrões para escrever nossos teste.

	Precisamos importar o pacote **testing**.
	Nossos arquivos de teste devem ter o sufixo **_test** antes da extensão.
	As funções devem começar com Test e devem tem o parâmetro ** \*testing.T**.

vamos ver um exemplo, criamos uma nova pasta chamada calculo *$GOPATH/src/github.com/renatosuero/calculo*.
```go
//arquivo main.go
package main
import "fmt"
func main(){
	fmt.Println(Soma(40,2)
}
func Soma(x,y int)int{
	return x + y
}
```
```go
//arquivo main_test.go
package main
import "testing"
func TestSoma(t *testing.T){
	n := Soma(600, 66)
	if n != 666 {
		t.Error("Resultado diferente do esperado")
	}
}
```

Para executar nossos testes executamos **go test**, há dois parâmetros que podemos passar junto ao comando -v *verbose* para mais detalhes e *-cover* para mostrar a porcentagem da cobertura dos testes. Importante, *go test* procura e executa os arquivos *_test.go*, se se criar seu projeto com packages, pode executar **go test ./...** desta forma ele irá procurar nos diretórios.

### Table test
```go
//arquivo main_test.go
package main
import "testing"
func TestSoma(t *testing.T){
	data := []struct{
		x,y,result int
		}{
			{15,16,31},
			{10,5,15},
			{400,255,655},
			}
	for _,row := range data{
		n := Soma(row.x, row.y)
		if n != row.result {
			t.Errof("A soma de (%d+%d) deveveria ser: %d, mas o resultado foi %d",row.x,row.y,row.result,n)
		}
	}
}
```
---
