## Variáveis
#### Go permite definir variáveis com os seguintes tipos:

lógicos para valores do tipo bool, ou seja, true ou false; Numéricos para valores do tipo int,float,etc..; Carácteres para valores do tipo string,ou seja, textos;

Existe algumas formas para definir variáveis,sendo elas:

```go
// Este é a forma que você pode estar acostumado.
var nome tipo //var age int

//Definindo múltiplas variáveis do mesmo tipo.Fazemos separando elas por , (vírgula).
var var_nome1, var_nome2 tipo //var x,y,z int

//Podemos definir uma variável com um valor inicial
var nome tipo = valor //var idade int = 30

//Também serve para múltiplas variáveis
var var_name1,var_name2 tipo = valor,valor //var x,y int = 10,20

//Inferência de tipos, quando a variável tiver um valor inicial, podemos omitir seu tipo.
var name = valor //var iadde = 30

//Também serve para múltiplas variáveis
var name1,name2 = valor1,valor2 //var x,y = 10,20
```
Existe uma outra forma para definir variáveis, mas esta tem as seguintes regras:

    Não pode ser usado fora de uma função;
    É obrigatório ter um valor inicial;

```go
//Não é obrigatório estar dentro da função main, mas dentro de alguma.
func main(){
  idage := 30
}
```

Se quiser ignorar o valor de uma pode ser feito usando **_**. Ainda não fará sentido usar isto, mas no futuro entenderá.Coloquei aqui apenas porque estou falando sobre variáveis e quis cobrir todos os casos.
```go
_,idade := 10,30
```
Desta forma apenas a variável idade terá um valor que será 30, o valor 10 foi ignorado.Isto fará sentido quando falar sobre retorno de funções.

### Constantes

Podemos usar string,números e valores boleanos.
```go
//Usamos a palavra reservada const,obviamente precisamos definir um valor para a constante.
const name = valor //const Pi = 3.1415926

//Se quiser atribuir o tipo da constante,é permitido
const name tipo = valor //const Pi float32 = 3.1415926
```
Podemos criar um grupo de variáveis,constantes e imports com tipos diferentes. Esta é uma forma bastante comum em projetos.
```go
//Podemos definir desta forma sem um valor inicial
var (
  nome string
  idade int
)
//Também podemos definir a variável com um valor inicial
var (
  nome = "Renato Suero"
  idade = 31
)
import (
  "fmt"
  "errors"
)
const (
  idade = 30
  name = "Renato Suero"
)
```
Os tipos aceitos são:

    bool 	string 	int 	int8 	int16
    int32 	int64 	uint 	uint8 	uint16
    uint32 	uint64 	uintptr 	byte 	rune
    float32 	float64 	complex64 	complex128 	

Variáveis que inicem sem valor terão os seguintes valores, o valor *null/nil* em go muda de acordo com o tipo da variável:

    0 para tipos numéricos
    “” para string
    false para bool
___
