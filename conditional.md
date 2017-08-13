## Estrutura Condicional

>Blocos de instruções em GO são C-style, ou seja, está entre {} #If

Não há novidade neste comando para quem já sabe programar. Podemos omitir os parenteses *(* *)* da condição e se o **if** não tiver próxima condição para o fluxo ou o bloco terminar com break, goto ou return é desnecessário a instrução else.
```go
age := 30
if age == 30{
  fmt.Println("é 30")
}

///Usando o return
var resultado int
if 1+1 == 2{
  resultado = 10
  return resultado 
}

///Exemplo com else
idade = 30
if idade > 18{
  fmt.Println("Você já pode beber cerveja")
}else{
  fmt.Println("Fica no leite bebê")
}

///Else if também temos um exemplo
linguagem = "GO"
if linguagem == "Java" {
  fmt.Println("Hum.... precisa de mais memória")
}else if linguagem == "GO" {
  fmt.Println("Parabéns GO te trará muitas felicidades")
}else{
  fmt.Println("Eita.... só não me fala que é ASP")
}
```

### Switch 
Também não temos novidades neste comando.
```
linguagem = "GO"
switch linguagem {
  case "Java":
    fmt.Println("Memória por favor")
  case "PHP":
    fmt.Println("Fazemos fazer spaghetti")
  case "GO":
    fmt.Println("Yeah")
}
```
Também temos um "else", usando o comando default.
```go
linguagem = "GO"
switch linguagem {
  case "Java":
    fmt.Println("Memória por favor")
  case "PHP":
    fmt.Println("Fazemos fazer spaghetti")
  case "GO":
    fmt.Println("Yeah")
  case default:
    fmt.Println("Eita.... começo a pensar que é ASP")
}
```
___