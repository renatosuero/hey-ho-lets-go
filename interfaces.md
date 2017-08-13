## Interfaces
Interfaces nada mais são que um tipo de dado, que possui comportamentos.Quando um tipo implementa todos os métodos da interface, automaticamente podemos usá-lo onde o tipo interface for necessário.
```go
package main
import (
	"fmt"
)
type Operacao interface{
	Calcular() float64
	Resultado() 
}
type Soma struct{
	X,Y float64
}
func (s Soma) Calcular()float64{
	return s.X + s.Y
}
func (s Soma) Resultado(){
   fmt.Println(s.Calcular());
}
type Sub struct{
	X,Y float64
}
func (s Sub) Calcular()float64{
	return s.X - s.Y
}
func (s Sub) Resultado(){
   fmt.Println(s.Calcular());
}
//O tipo do dado é Operacao ou seja é uma interface
func execCalculo(o Operacao){
	o.Resultado();
}

func main() {
	soma := Soma{10,20}
	sub := Sub{32,20}
	//O array é do tipo Operacao, ou seja,structs que possuem os métodos implementados podem ser adicionados
	dados := []Operacao{soma,sub}
	for _,ope := range dados{
		execCalculo(ope);
	}
}
```
A struct Soma e Sub tem os  métodos Calcular Resultado,sendo assim podemos usá-las em funções onde o Tipo de dados é Operacao. Como podem ver podemos criar um novo array do tipo Operacao e adicionarmos structs Soma e Sub sem problemas.

---
