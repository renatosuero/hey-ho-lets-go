## Métodos

Um método nada mais é do que uma função com um Receiver, em outras palavras ela "pertence" a uma struct.A sintaxe dela é
```go
func (name Struct) nameFunction(params) returnValue {
	//Seu código
}
```
Um exemplo real para ficar mais claro:
```go
type Person struct {
	Name, Surname string
}

func (person Person) fullName() string {
	return person.Name + " " + person.Surname
}
func main() {
	renato := Person{"Renato", "Suero"}
	fmt.Print(renato.fullName());
}
```
Desta forma passamos uma cópia da struct para o método,como veremos a seguir:
```go
type Person struct {
	Name, Surname string
}

func (person Person) fullName() string {
	return person.Name + " " + person.Surname
}
func (person Person) setName(newName string) {
	person.Name = newName
}
func main() {
	renato := Person{"Renato", "Suero"}
	fmt.Println(renato.fullName());
	renato.setName("José Renato");
	fmt.Println(renato.fullName());
}

//Renato Suero
//Renato Suero
```
Como podem ver não alteramos o valor da nossa struct, se quiserem alterar o valor é necessário o uso de ponteiros, no exemplo abaixo eu só adiciono um **\*** no segundo método (setName) fazendo ele receber o endereço em memória da nossa struct.
```go

type Person struct {
	Name, Surname string
}

func (person Person) fullName() string {
	return person.Name + " " + person.Surname
}
func (person *Pessoa) setName(newName string) {
	person.Name = newName
}
func main() {
	renato := Person{"Renato", "Suero"}
	fmt.Println(renato.fullName());
	renato.setName("José Renato");
	fmt.Println(renato.fullName());
}
//Renato Suero
//José Renato Suero
```
___
