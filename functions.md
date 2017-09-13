## Funções
Funções em GO são first-class citzen, ou seja podemos fazer qualquer operação que a linguagem permita. Podemos passar como parâmetro pra outra,atribuir a uma variável,usar como valor de retorno e usar em structs.
Aqui uma diferença que já deve ter sido notada, funções em GO são criadas com o comando func. A sintaxe básica para funções é

    func nomeFuncao(parâmetro tipo) retorno{ //Aqui o código da função }

```go
//Primeiro um exemplo básico sem parâmetros e retorno.
func exibeMsg() {
	fmt.Println("Esta é uma função")
} 

//Agora com parâmetro
func exibeMsg(nome string) {
	fmt.Println("Olá ", nome)
}


//Com retornos
func soma(x int, y int) int {
	return x + y
}
//Se os parametros são do mesmo tipo poderia ser feito 
func soma(x, y int) int {
	return x + y
}
```
Go permite retorno de múltiplos valores, como verá no exemplo a seguir: [Playground](https://play.golang.org/p/vorDGISRdD)
```go
func main() {
	valor, msg := soma(10, 10)
	//se não desejar algum valor pode usar o carácter _ (underscore),assim ignorando o valor retornado
	//_, msg := soma(10,10)
	fmt.Println(valor) // 20
	fmt.Println(msg)   // Impar
}
func soma(x int, y int) (int, string) {
	total := x + y
	var isOdd string
	if total%2 == 0 {
		isOdd = "Par"
	} else {
		isOdd = "Impar"
	}
	return total, isOdd
}
```
Outra coisa legal é que podemos criar retorno com parâmetros nomeados. [Playground](https://play.golang.org/p/iAPbmZa64O)
```go
func main() {
	valor, msg := soma(10, 10)
	fmt.Println(valor) // 20
	fmt.Println(msg)   // Par
}
func soma(x, y int) (total int, isOdd string) {
	total = x + y
	if total%2 == 0 {
		isOdd = "Par"
	} else {
		isOdd = "Impar"
	}
	return
}
```
Go também possui closure. [Playground](https://play.golang.org/p/wq9Zn0qHG2)
```go
add := func(x, y int) int {
    return x + y
}
fmt.Println(add(10, 20)) // 30
```

Também é possível criar funções com número parâmetros variável, ou seja, a função pode receber um ou mais valores separado por **,**. [Playground](https://play.golang.org/p/Z07mjwEnkA) 
```go
func sum(values ...int)int{ 
    total := 0 
    for_, val := range values { 
        total += val 
    } 
    return total 
} 

sum(3) // 3
sum(10,20,5) // 35
```
Funções anônimas, são interessantes deseja definir uma função em linha sem ter que nomeá-la,veja um exemplo: [Playground](https://play.golang.org/p/Od51DUaRA5)
```go
func mutiplicadorBase(base int) func(int) int {
	return func(por int) int {
		return base * por
	}
}

mutiplicarPor := mutiplicadorBase(6)
fmt.Println(mutiplicarPor(2)) // 12
fmt.Println(mutiplicarPor(7)) // 42
fmt.Println(mutiplicarPor(9)) // 52
```
___
