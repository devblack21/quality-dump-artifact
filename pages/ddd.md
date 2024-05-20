# DDD - Domain Driven Design (Eric Evans)

## Descrição Técnica 

> É uma forma de desenvolver software com o foco no coração da aplicação - oque chamamos de 
> domínio - tendo o objetivo de entender suas regras, processos e complexidades, 
> separando-as assim de outros pontos complexos que normalmente são adicionados durante 
> o processo de desenvolvimento.

## Conceitos 

- [Linguagem Ubíqua](#linguagem-ubíqua) 
- [Domínio](#domínio)
- [Sub-Domínio](#sub-domínio)  
- [Bounded Context (Contextos delimitados)](#bounded-context-contextos-delimitados)  
- [Context Mapping (Visão estratégica)](#context-mapping-visão-estratégica)
- [Modelagem de Dominios](#modelagem-de-dominios)

<br>

## Linguagem Ubíqua

A Linguagem Ubíqua é um conceito central de DDD. Ela consistem de um conjunto de termos que devem
ser plenamente entendidos por todos os envolvidos no projeto (por Especialista do dominio e por Desenvolvedores).

Por exemplo:

- Em um sistema de vendas, ao se falar no termo *ordemVenda* todos os envolvidos devem saber que esse termo tem o 
mesmo significado, tanto o Desenvolvedor, PO, QA, Gerente e etc...

#### Barreiras

Extrair a linguagem ubíqua, é uma tarefa bem desafiadora, pois isso só é possivel através de muito envolvimento dos 
especialistas de dominio, equipe técnica e os demais envolvidos no projeto. Onde é definido quais vão ser os termos 
utilizados para cada coisa no projeto.

Por exemplo:

Em um sistema de livraria, os envolvidos levantaram o seguinte mapa de linguagem ubíqua:

    Livro : Representa o livro fisico que será alugado
    Locação : Representa o aluguel dos livros feito pelo cliente
    Cliente : Representa o cliente que faz as locações dos livros na livraria
    Pagamento : Representa o pagemento feito no momento da locação

Nota-se que o exemplo acima é semelhante ao um dicionário.

OBS: é uma boa prática ter uma documentação com o dicionário que descreve oque cada termo
representa no projeto. Assim garatimos que todos os envolvidos conversem a mesma lingua. 

Pode e dever ser utilizado a técnica de  <b><a href=""> Event-Storming </a></b> para facilitar na captação dos termos utilizados por
todos os envovidos no projeto.

## Domínio

Dominio é problema que estamos tentando resolver, tudo que é importante para o software, o motivo dele existir.

Por exemplo:

    Em um sistema de aluguel de veiculos, temos os seguintes dominios:

        - Veiculo
        - Aluguel
        - Cliente

Obviamente tem muito mais dominios, mas os mais importantes são esses citados acima, pois sem eles não existiria o sistema (chamados de <b>Core-Domain</b>),
a regra de negócio é baseada no <b>Aluguel</b>, que o mesmo só existe por conta de <b>Veículos</b> e <b>Cliente</b>.


### Core Domain

É o principal para a existencia do sistema, é oque da sentido ao resto estar existindo.

## Sub-Domínio

Sub-Domínio é a subparte do Domínio. Independentemente do tamanho da solução, todo Domínio sempre poderá ser dividido em Sub-Domínios, 
com isso, podemos dividir a complexidade do Domínio da companhia em partes menores, e teremos especialistas em Domínio que vão 
entender muito bem os aspectos de negócio por se tratar de um Subdomínio específico.

Ou seja, no mesmo exemplo da loja de aluguel de Veículos, temos o Domínio Veículo, e a companhia começou a crescer demais...
Assim aumentado de forma exponencial sua frota de carros, contudo o controle dessa frota ficou cada vez mais custoso, pois cada veiculo tem sua 
manutenção e isso deve ser controlado sistematicamente. Assim nascendo mais um Dominio para a loja, o Dominio de <b>Manutenção de Veiculos</b>.


Existem dois tipos de Sub-Domínio: <b>Suporte</b> e <b>Genérico</b>.

### Sub-Domínio de Suporte

É o Dominio que complementa o Dominio principal (<b>Core-Domain</b>), sem ele, seu Domínio principal não pode ser bem-sucedido, portanto, ele é 
muito importante, e exigirá desenvolvimento interno ou terceirização, pois não existe solução pronta para implementar.

Um exemplo disso é a na solução de Manutenção de Veículos, qual é o Core Domain? Se você falou que é Manutenção, vc acertou! Porém, para 
esse Domínio existir, é necessario existir o Domínio de Veiculo primeiro, assim podemos dizer que <b>Veículo </b>é um Sub-Domínio de <b>Manutenção</b>.

### Sub-Domínio Genérico

É tipicamente uma solução pronta, mas também pode ser terceirizado ou até mesmo desenvolvido internamente. Ele não traz uma regra específica
para o seu negócio principal, ou seja, na maioria dos casos poderíamos contratar como um serviço (Não tem um grande diferencial competitivo para a empresa).

Um exemplo disso são os Gateways de pagamento, onde é preciso ter ele para o funcionamento da regra de negócio principal, porém podemos 
utilizar um sistema externo para compor. No caso da loja de aluguel de carro, para finalizar o <b>Aluguel</b> será necessario utilizar 
o <b><i>Gateway de Pagamento</b></i> para realizar o <b>Pagamento</b> do <b>Aluguel</b>.

    OBS: note que não interessa para a Loja qual é o dominio e como é feito o Pagamento, ou seja, não tem um diferencial competitivo.

## Bounded Context (Contextos delimitados)

## Context Mapping (Visão estratégica)

## Modelagem de Dominios

### Entities

### Value Objects

### Aggregate

### Domain Service

### Domain Events 

### Modules

### Factories

