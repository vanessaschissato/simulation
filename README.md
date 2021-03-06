# simulation

# Parte 1 (Configurando ambiente e executando)

## Leitura

* Tutorial (tour) da linguagem GO: https://tour.golang.org/welcome/1
* Boas práticas: https://golang.org/doc/effective_go.html (pelo menos o comecinho e importante)

## Instalação GO: https://golang.org/doc/install

	tar -C /usr/local -xzf go$VERSION.$OS-$ARCH.tar.gz
	export PATH=$PATH:/usr/local/go/bin

## Configuração workspace: https://golang.org/doc/code.html

### Criação da estrutura de pastas:

	vschissato@vschissato:~$ tree workspace-golang/
	workspace-golang/
	├── bin       <- executáveis (entregáveis)
	├── pkg       <- pacotes de bibliotecas
	└── src       <- código fonte

### Criação das variáveis de ambiente

	export GOPATH=$HOME/workspace-golang
	export PATH=$PATH:$GOPATH/bin (conveniência)
	
### Download do projeto:
	
	go get github.com/vanessaschissato/simulation
	
	Resultado (código baixado, compilado e instalado):
	vschissato@vschissato:~$ tree workspace-golang/
	workspace-golang/
	├── bin
	│   └── simulation                           <- executável (entregável), linkagem estática com a biblioteca sellerapi.a (portanto, entregável é auto funcional, único arquivo que precisa ser deployado)
	├── pkg
	│   └── linux_amd64
	│       └── github.com
	│           └── nessauepa
	│               └── simulation
	│                   └── sellerapi.a          <- biblioteca seller api client
	└── src
	    └── github.com
	        └── nessauepa
	            └── simulation                    
	                ├── README.md
	                ├── sellerapi
	                │   ├── simulation.go        <- Fonte da biblioteca seller api client com codigos ref. a simulation
	                │   └── simulation_test.go   <- Teste unitário do arquivo respectivo
	                └── simulation.go            <- Arquivo principal (importa a biblioteca sellerapi)

## Build e install com GO Tools: https://golang.org/cmd/go/

	go install github.com/vanessaschissato/simulation
	simulation

# Parte 2 (escrevendo código)


## Formatação de código:

	go fmt github.com/vanessaschissato/simulation
	
## Organização de código: https://blog.golang.org/organizing-go-code

## Testes unitários

### Convenções de testes unitários: https://golang.org/doc/code.html#Testing

	go test github.com/vanessaschissato/simulation

#### Cobertura de testes 
	Calcula cobertura dos testes e exibe no browser (UI)

	go test github.com/vanessaschissato/simulation -coverprofile=coverage.out
	go tool cover -html=coverage.out 

## Documentação: https://golang.org/doc/effective_go.html#commentary

	$ godoc github.com/vanessaschissato/simulation/sellerapi
	PACKAGE DOCUMENTATION
	
	package sellerapi
	    import "github.com/vanessaschissato/simulation/sellerapi"
	
	    Package sellerapi implements a client to the Seller API.
	
	FUNCTIONS
	
	func Simulate() string
	    Simulate make a order simulation
