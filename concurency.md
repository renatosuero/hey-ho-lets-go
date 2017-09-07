## Concorrência
> Concurrency is not parallelism.  

Outras linguagens possuem as threads para isso, mas não são exatamente a mesma feature.Elas são mapeadas diretamente para as threads do SO, e estas são relativamente pesadas.Isso por tem seu stack de tamanho fixo. Isso diminui o número de thread devido ao aumento da sobrecarga de memória. Go usa **goroutine** que tem uma stack segmentado e cresce conforme a demanda, estas são chamadas *Green Threads*, quem as gerencia é linguagem e não o SO.  

### Goroutine
A primeira coisa que você precisa saber é que para usar concorrência,você precisa adicionar a palavra reservada **go** antes da chamada da função. Como podem ver no exemplo
```go
func main(){
	printMsg("Renato Suero")
	go printMsg("Golang")
}
func printMsg(msg string){
	fmt.Println(msg)
}
```
> Importante lembrar que as goroutines dependem da função main, ou seja se ela terminar antes as goroutines morrem.  
### Channels
> Do not communicate by sharing memory; instead, share memory by communicating.  

Channel é a feature para as goroutines se comunicarem, uma das formas de se evitar **race conditions**.  
Para interagirmos com um canal usamos o operador <- *arrow operation* a posição do canal em relação à seta indica a direção do fluxo de comunicação.
```go
//Criando um channel
canal := make(chan int)
//Enviando um valor para o canal
canal <- 666

//Recebendo valor do canal
value := <-canal
```
### Buffer
Canais pode sem criados como buffer. Isso faz com que o operador de envio/recebimento não seja bloqueado até completar o buffer.  
```go
canal := make(chan int,3)
```
Se de alguma forma tentarmos enviar/receber mais dados que o tamanho do **buffer** o ambiente de execução detectará o **deadlock** e encerrará a execução do programa.  
É muito importante que o lado que envia indique que não enviará mais dados pelo canal. Para isso existe a função Close(channel).  
```go
func receiveChannel(canal chan int){
	c <-666
	Close(canal)
}
```
No lado que recebe o channel precisamos indentificar que o mesmo foi fechado. O perador <- retorna 2 valores (o valor lido e um bool que indica se o valor foi lido). Quando este valor for **false** significa que o channel foi fechado.  
```go
channel,isClosed := <-canal
```
> Deadlocks no contexto de sistemas operacionais (SO), refere-se a uma situação em que ocorre um impasse, e dois ou mais processos ficam impedidos de continuar suas execuções - ou seja, ficam bloqueados, esperando uns pelos outros.  

```go
func test(c chan<-int){}  //Apenas envia um valor
func test2(c <-chan int){} //Apenas recebe um valor
```
### Select
Quando precisamos interagir com múltiplos canais, utilizamos o **select**, outro aplicação é termos tempo para executarmos, neste caso usamos timeouts.  
```go
select {
case value:= <-channel1:
case value2 := <-channel2:
case <- time.After(time.Second * 10): //Esta função retorna um channel
        fmt.Println("timeout")
default:
}
```
### WaitGroup
Go possui um tipo chamado **WaitGroup** do pacote sync, que nos ajuda a controlar as goroutines em execução, evitando que a função **main** termine e encerre a aplicação.  
```go
import "sync"
func main(){
var wg sync.WaigGroup
wg.Add(2)
	for i:=0;i<=2;i++{
		go showValue(&wg,i) 
	}
	wg.Wait()
}
func showValue(wg *sync.Value,value int){
	fmt.Println(value)
	defer wg.Done()
}
```
### Atomic

### Mutex


___
