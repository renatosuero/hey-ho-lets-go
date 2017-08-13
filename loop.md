## Repetições
    Aqui temos uma novidade, GO não tem o **while**. 
### For
A única novidade é a falta do while e como o for "imita" o while.
```go
//For básico
for valor; condição; incremento{ // for i:=0; i<10; i++{
}
//Podemos criar for sem o incremento
for valor; condição;{//for  contador < 5{
}
//for estilo while
contador = 0
for  contador < 5{
  fmt.Println(contador)
 contador++
}
//for sem condições, importante adicionar alguma condição para sair deste loop, este seria o mesmo que while true.
for {
 fmt.Println("Este é o loop da morte!"))
}
```
### Range
Range é a forma para um loop interagir com um slice ou map
```go
var numeros = []int{1,2,3,4,5,6,7,8,9}
for index, value := range numeros {
  fmt.Printf("Indice => %d e valor => %d",index,value)
}
```
### Goto
Este é um cara que nem sabia se falaria,basicamente o que ele faz é mudar o fluxo do teu código para um label previamente definido. *Tome cuidado se decidir usar*.
```go
//Retirado da documentação
func myFunc()	{
	i	:=	0
Here://label ends with	":"
		fmt.Println(i)
		i++
	goto Here //jump to label "Here"
}
```
___
