## Structs
Uma struct é uma coleção de campos/propriedades. Você pode definir novos tipos com structs.A síntaxe para criar uma struct é:
```go
type Name struct {
    //Variáveis, se for do mesmo tipo pode usar a regra x,y int
}

type Person struct {
	Name, Surname string
	Age           int
}
```
Podemos atribuir valores iniciais na struct, você pode omitir o nome dos campos, GO irá tentar identificá-los pelo seu tipo.
```go
type Person struct {
	Name string
	Age  int
}

person1 := Person{Name: "Renato", Age: 30}
person2 := Person{"Marina", 30}
```
Struct não possui **`Getters`** e **`Setters`** , para acessar um campo/propriedade, usamos a síntaxe *`Struct.campo`*. Usando o exemplo acima para economizar códigos.
```go
person.Name = "Renato Suero"
fmt.Println(person.Name)
```
Structs suporta composição de tipos, ou seja, podemos compor um tipo herdando de outro,como no exemplo abaixo:
```go
type Person struct {
	Name string
	Age  int
}
type Developer struct {
	Person
	Database, Language string
}

renato := Developer{}
renato.Name = "Renato Suero"
renato.Age = 31
renato.Database = "PostgreSQL"
renato.Language = "GO"
```
### Ponteiros 
GO possui ponteiros, mas não são ponteiros aritméticos. Por padrão GO passa argumento por valor, ou seja, copiando o argumento. Se você quer passar valor por referência, você precisa usar ponteiros ou usar estruturas usando valores referenciados em Slices e Maps. Para acessar uma variável em memória precisamos de seu endereço, podemos usar **`&variavel`** para tê-lo. Para ler seu valor usamos **`*variavel`**. [Playground](https://play.golang.org/p/lVeYEi6dtY)
```go
func main() {
	x := 10
	zero(x) // 10
	fmt.Println(x)
	zero2(&x) // 0
	fmt.Println(x)
}
func zero(x int) {
	fmt.Println(x) // 10
	x = 0
}
func zero2(x *int) {
	fmt.Println(x) // 0x10410020
	*x = 0
}

```
___
