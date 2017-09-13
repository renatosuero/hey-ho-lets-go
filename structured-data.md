## Dados Compostos
#### Array
Array tem um tamanho fixo, mas pode ser omitido se iniciado com valores.
```go
var dados [4]int
//Atribuindo valores
dados := [4]int{1, 2, 3, 4}

//Sem definir o tamanho,Go calcula para você
dados := [...]int{1, 2, 3, 4}

///Também podemos criar array multidimensional
dados := [2][2]int{{1, 2},{3, 4}}
```
### Slice
É um array que seu tamanho pode ser alterado, ele não te obriga a definir um tamanho. Por esta razão suas operações são mais pesadas que um array. Regra geral, se souber o tamanho use **array**.
```go
var dados []int{}

//Podemos omitir as chaves
var dados []int
```
Para adicionar o valor no slice usamos append.
```go
var dados []int
dados = append(dados, 10)

dados := []int{}
dados = append(dados, 10)
``` 
Quando criamos um slice sem valores o seu tamanho inicial é 0, podemos usar o make e assim já definir um tamanho inicial ao slice.
```go
var dados = make([]int, 10)
fmt.Println(len(dados))
```
Slice também tem o copy, mesmo que o tamanho seja diferente
```go
slice1 := []int{1, 2, 3}
slice2 := make([]int, 2)
copy(slice2, slice1)
fmt.Println(slice1, slice2)
```
### Map

Maps em algumas linguagens são chamados Dicionários ou Hash.
Podemos usar o make para definirmos um map vazio.
```go
var x = make(map[string]int)
x["idade"] = 30
fmt.Println(x["idade"])
```
Também podemos criar maps com valores iniciais.
```go
x := map[string]int{"idade": 30}
fmt.Println(x["idade"])
```
___
