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

<br>

## Linguagem Ubíqua

A Linguagem Ubíqua é um conceito central de DDD. Ela consistem de um conjunto de termos que devem
ser plenamente entendidos por todos os envolvidos no projeto (por Especialista do dominio e por Desenvolvedores)

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

Nota-se que o exemplo acima é semelhante ao um dicionário

OBS: é uma boa prática ter uma documentação com o dicionário que descreve oque cada termo
representa no projeto. Assim garatimos que todos os envolvidos conversem a mesma lingua. 

Pode e dever ser utilizado a técnica de  <b><a href=""> Event-Storming </a></b> para facilitar na captação dos termos utilizados por
todos os envovidos no projeto.

## Domínio

## Sub-Domínio

## Bounded Context (Contextos delimitados)

## Context Mapping (Visão estratégica)