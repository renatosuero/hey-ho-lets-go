## Error
Em GO o **error** é um tipo de dado assim como uma string,int,etc..., que decidi falar só agora pois já conhecemos as funções.  
Isso pode parecer estranho no começo para alguns, mas depois vão ver que isso é muito útil, pois podemos sempre garantir que o retorno da função vem com o valor desejado, e se houver erro conseguimos detectar e assim tomar uma decisão de como proceder. Esse cara faz tanto sentido que possui duas referências no [GO proverbs](https://go-proverbs.github.io).
```go
_, err := os.Open("file.txt")
if err != nil{
	log.Fatal(err)
}
```
```go
//Também podemos criar nossas mensagens de erro
import "errors"
err := errors.New("Mensagem de erro personalizada")
if err != nil {
	log.Fatal(err)
}
```

Por convenção o error é o último valor retornado na função.Como no exemplo:
```go
import "errors"
import "log"
func division(x,y int) (int,err){
	if y == 0{
		err := errors.New("Não é possível fazer divisão por zero.")
		return 0,err
	}else{
		result := x/y
		return result,nil
	}
}

result,err := division(10,0)
if err != nil {
	log.Fatal(err)
}
```
---
