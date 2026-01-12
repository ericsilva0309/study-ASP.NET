1. [O que é .NET?](#o-que-é-net)
2. [Qual a diferença entre .NET e ASP.NET?](#qual-a-diferença-entre-net-e-aspnet)
3. [O que é ASP.NET Core e por que ele é usado hoje em vez do ASP.NET antigo?](#o-que-é-aspnet-core-e-por-que-ele-é-usado-hoje-em-vez-do-aspnet-antigo)
4. [O que é Dependency Injection (DI)?](#o-que-é-dependency-injection-di)
5. [No seu projeto, você usou Injeção de Dependência?](#no-seu-projeto-você-usou-injeção-de-dependência)
6. [Diferença entre Singleton, Scoped e Transient](#diferença-entre-singleton-scoped-e-transient)
7. [O que é Polimorfismo?](#o-que-é-polimorfismo)
8. [Diferença entre Interface e Classe Abstrata](#diferença-entre-interface-e-classe-abstrata)
9. [O que é um ORM no .NET?](#o-que-é-um-orm-no-net)
10. [Diferença entre Entity Framework e Dapper](#diferença-entre-entity-framework-e-dapper)
11. [O que é uma API REST?](#o-que-é-uma-api-rest)
12. [O que é a AWS e quais serviços você já utilizou?](#o-que-é-a-aws-e-quais-serviços-você-já-utilizou)
13. [O que é Arquitetura em Camadas / Clean Architecture?](#o-que-é-arquitetura-em-camadas--clean-architecture)
14. [O que é RabbitMQ e por que ele foi usado?](#o-que-é-rabbitmq-e-por-que-ele-foi-usado)
15. [Producer, Consumer e Queue](#producer-consumer-e-queue)
16. [O que é uma Exchange no RabbitMQ?](#o-que-é-uma-exchange-no-rabbitmq)
17. [O que é Routing Key?](#o-que-é-routing-key)
18. [Tipos de Exchange](#tipos-de-exchange)
19. [Por que RabbitMQ ajuda na escalabilidade?](#por-que-rabbitmq-ajuda-na-escalabilidade)

---

## O que é .NET?

.NET é uma plataforma da Microsoft para desenvolvimento de aplicações.
Ela fornece um runtime, bibliotecas e ferramentas, suporta várias linguagens (sendo C# a principal) e é usada para criar aplicações web, APIs, desktop e outros tipos de sistemas.

---

## Qual a diferença entre .NET e ASP.NET?

.NET é a plataforma.
ASP.NET (ou ASP.NET Core) é o framework usado dentro do .NET para criar aplicações web e APIs.

---

## O que é ASP.NET Core e por que ele é usado hoje em vez do ASP.NET antigo?

ASP.NET Core é a versão moderna do ASP.NET.
Ele é multiplataforma, tem melhor desempenho e é o padrão atual para desenvolvimento de aplicações web e APIs.

---

## O que é Dependency Injection (DI)?

Dependency Injection é um padrão onde uma classe **recebe suas dependências prontas**, geralmente via construtor, ao invés de criá-las diretamente.

Em vez de:

```csharp
var person = new Person();
```

A dependência é criada em outro local e injetada na classe.

---

## No seu projeto, você usou Injeção de Dependência?

Sim. No projeto foi utilizada Injeção de Dependência separando **Controller, Service e Repository**.

* O Controller recebe o Service via construtor
* O Service recebe o Repository
* Nenhuma camada cria suas dependências diretamente

Tudo é configurado no container de DI, reduzindo acoplamento, facilitando testes e mantendo uma boa separação de responsabilidades.

---

## Diferença entre Singleton, Scoped e Transient

Esses conceitos definem o **tempo de vida** de um serviço no container de DI.

### Transient

* Uma nova instância é criada toda vez que o serviço é solicitado
* Usado para serviços simples e stateless

### Scoped

* Uma instância por requisição HTTP
* Controller, Service e Repository compartilham a mesma instância durante a requisição
* Muito usado com banco de dados

### Singleton

* Uma única instância para toda a aplicação
* Criada na primeira vez que é solicitada
* Usado para serviços imutáveis, cache e configurações

---

## O que é Polimorfismo?

Polimorfismo é quando diferentes classes implementam o mesmo método, mas com comportamentos diferentes.

Exemplo: um método `Voar()` pode existir em várias classes, mas cada uma executa esse método de forma diferente.

---

## Diferença entre Interface e Classe Abstrata

### Interface

* Define **o que** uma classe deve fazer
* Não define **como**
* A classe que implementa é obrigada a fornecer a implementação

### Classe Abstrata

* Pode conter código comum entre as classes
* Usada quando existe lógica que deve ser reaproveitada

---

## O que é um ORM no .NET?

ORM é uma ferramenta que mapeia objetos do código para tabelas do banco de dados, facilitando o acesso aos dados sem escrever SQL manualmente o tempo todo.

No .NET:

* **Entity Framework**: ORM completo
* **Dapper**: Micro-ORM focado em performance

---

## Diferença entre Entity Framework e Dapper

* **Dapper** é focado em performance e exige escrita manual de SQL
* **Entity Framework** é focado em produtividade, abstrai o SQL e oferece mais funcionalidades

---

## O que é uma API REST?

É uma interface de comunicação entre sistemas baseada em HTTP, que segue os princípios da arquitetura REST.

Principais verbos HTTP:

* GET
* POST
* PUT
* PATCH
* DELETE

---

## O que é a AWS e quais serviços você já utilizou?

A AWS é uma plataforma de computação em nuvem.

Experiência prática com:

* Lambda
* Step Functions
* API Gateway
* DynamoDB
* CloudWatch
* Cognito
* SQS
* Amplify (deploy do front-end)
* IAM
* CodeCommit

Projetos serverless e full stack utilizando esses serviços.

---

## O que é Arquitetura em Camadas / Clean Architecture?

Arquitetura em camadas organiza o sistema separando responsabilidades.

Estrutura utilizada:

* **Domain**: regras de negócio
* **Application**: casos de uso
* **Infrastructure**: banco de dados e integrações
* **Web**: exposição via API

Isso facilita manutenção, testes e evolução do sistema.

---

## O que é RabbitMQ e por que ele foi usado?

RabbitMQ é um broker de mensagens que permite comunicação assíncrona entre sistemas usando filas.

Foi utilizado para permitir que eventos fossem processados de forma assíncrona e desacoplada.

---

## Producer, Consumer e Queue

* **Producer**: envia mensagens
* **Consumer**: consome mensagens
* **Queue**: armazena mensagens até que sejam processadas

---

## O que é uma Exchange no RabbitMQ?

Exchange é o componente responsável por receber mensagens dos producers e rotear essas mensagens para as filas conforme regras definidas.

---

## O que é Routing Key?

Routing key é uma chave usada pela exchange para decidir para qual fila a mensagem será encaminhada.

---

## Tipos de Exchange

* Fanout (envia para todas as filas)
* Direct (usa routing key)
* Topic (usa padrões de routing key)

---

## Por que RabbitMQ ajuda na escalabilidade?

RabbitMQ permite comunicação assíncrona e desacoplada.

Os produtores não precisam esperar os consumidores, e os consumidores podem ser escalados independentemente para processar mais mensagens.
