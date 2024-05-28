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

É um conceito razoalvelmente fácil de se explicar, porém pode ser extremamente complexo de se implementar. Tudo 
depende da visão global do domínio da aplicação.

<b>O que significa visão global do domínio?</b>

Ter uma visão global significa enxergar toda a extensão de seu domínio e eu não estou me referindo as camadas, estou me referindo ao negócio.

<b>Como ter uma visão global do negócio se a aplicação ainda não foi desenvolvida ou está em processo de desenvolvimento?</b>

É necessário lutar contra a IVSF “Irresistível Vontade de Sair Fazendo” e focar 
antes em mapear seus contextos e definir os Bounded Contexts “contextos delimitados”. 
Para determinar seus Bounded Contexts você precisa ter um bom conhecimento do negócio da empresa ou 
ter ao seu lado um <b>Domain Expert</b>.

### Domain Expert

É a pessoa que entende do negócio da empresa e vai apoiar os times de desenvolvimento na modelagem do domínio, 
definição das regras de negócio e etc. O domain expert também é responsável por definir a Ubiquitous Language
“Linguagem Ubíqua”.


### Rapida Introdução sobre Context Mapping 

Para a aplicação ter um bom design, uma fácil manutenção / extensibilidade e o domínio ser bem modelado é 
necessário focar em modelagem estratégica e para isso é 
importante preocupar-se com a integridade do modelo conforme o diagrama do Context Map apresenta.

Todos os conceitos do Context Map são importantes, é necessário compreender muito bem de cada um 
deles para termos condição de realizar uma boa modelagem.


### Big Ball of Mud - Bola de Lama

A grande bola de lama. Você pode ter uma em suas mãos neste momento.
Este conceito aborda vários aspectos negativos de sua aplicação, desde código macarrônico que 
fere os princípios do SOLID e Clean Code até uma entidade com muitas responsabilidades em um 
único contexto. Analise a imagem a seguir:


<p align="center">
    <img src="https://i0.wp.com/www.eduardopires.net.br/wp-content/uploads/2016/03/BBM.jpg?resize=404%2C255&ssl=1" width="350" title="hover text">
</p>

A entidade Produto possui diversos comportamentos, cada um destes comportamentos está ligado a 
uma intenção da aplicação, todas as intenções são relativas ao produto em si, porém imagine a
complexidade desta classe, quantas equipes de desenvolvimento estão compartilhando a mesma classe em comum.
A entidade Produto atende aspectos de Aquisição, Venda, Entrega, Estoque e etc.
Esse tipo de modelagem pode ser considerada um exemplo de Big Ball of Mud, pois
qualquer manutenção nessa entidade pode ocasionar impactos
sérios em diversos pontos da aplicação, é praticamente impossível de gerenciar as mudanças.

<b>Como resolver ou evitar este tipo de cenário?</b>

O DDD não é sobre dividir a aplicação em camadas responsáveis, o DDD é sobre modelar corretamente o domínio 
do seu negócio. Se sua aplicação possui uma única camada de domínio e esta camada concentra todas as entidades
do seu negócio você pode estar cometendo um grande erro de modelagem de domínio. Para aplicações que possuem
domínios muito complexos o ideal é aplicar o conceito de Bounded Context.


### Solução - Bounded Context 

Os contextos delimitados ou bounded contexts buscam delimitar o seu domínio complexo em contextos baseados nas
intenções do negócio. Isto significa que você deve delimitar as intenções de suas entidades
com base no contexto que ela pertence. Analise a imagem a seguir:  

<p align="center">
    <img src="https://i0.wp.com/www.eduardopires.net.br/wp-content/uploads/2016/03/BoundedContexts.jpg?resize=363%2C279&ssl=1" width="350" title="hover text">
</p>

O domínio foi subdividido em seis pedaços, ou melhor, em seis bounded contexts, um para cada intenção de 
negócio (Vendas, Entregas, Estoque etc.). Agora cada bounded context possui uma entidade Produto.
Cada versão da entidade Produto é diferente nos seis bounded contexts existentes. 
A entidade Produto possui comportamentos que atendem necessidades específicas de seu bounded context,
a única coisa em comum entre todas as entidades Produto é sua identidade, o ProdutoId no caso. 
A identidade em comum vai ajudar na persistência e na comunicação entre os bounded contexts.

Ou seja, Bounded Context é sobre a intenção e os comportamentos dentro daquele contexto.


<b>Representar a mesma entidade em diversos bounded contexts não seria duplicar o código?</b>

De forma alguma. Duplicar código é ter a mesma responsabilidade em trechos de código diferentes.
Neste caso existe uma segregação de comportamentos e intenções de uma entidade conforme o contexto
em que ela está. Não importa se a entidade é persistida na mesma tabela ou em tabelas diferentes, 
neste caso ambos os cenários são aceitos.

<b>Características importantes de um bounded context</b>

 - Cada bounded context pode possuir sua própria abordagem de arquitetura. Camadas de aplicação, persistência, infra-estrutura e etc.
 - A arquitetura de um bounded context não precisa estar necessariamente no padrão DDD (Domain Model) pode ser um modelo mais simples de 3 camadas, pode implementar CQRS, Event Sourcing e etc.
 - Cada bounded context pode possuir um meio próprio de persistência, sendo ele relacional, NoSQL, em memória / cache e etc.
 - Os bounded contexts podem se comunicar entre si de diversas maneiras, inclusive utilizando eventos de domínio “Domain Events” conectados em um “Event Bus”.
 - Cada bounded context possui sua própria Ubiquitous Language.
 - Cada bounded context pode ser desenvolvido por um time de desenvolvedores diferente. Não existe necessidade de um único time conhecer a implementação de todos os contextos, pelo contrário, por motivos de segurança o fonte de um bounded context pode ser restrito a um time específico.


Existem diversos patterns que descrevem o tipo de relacionamento entre os bounded contexts, <a href="ddd-patterns.md">clique aqui para saber mais...</a>

## Context Mapping (Visão estratégica)

## Modelagem de Dominios

### Entities

### Value Objects

### Aggregate

### Domain Service

### Domain Events 

### Modules

### Factories

