# Funções "Funcionais" em Python
Olá a todos, meu nome é John Cunha e sou estudante de Graduação em Ciência da Computação. Este é meu primeiro artigo escrito no Medium, então dêem uma relevada sobre a qualidade, prometo que vou tentar melhorar daqui pra frente 😁.

Como sou estudante de Computação nada mais lógico que trazer esse tema no artigo, mas calma que não irei começar a despejar teoria aqui. Como o título do artigo sugere, hoje irei trazer para vocês funções "funcionais" em Python e como utilizá-las, então vem comigo.

## Primeiro, o que são funções "funcionais"?
Durante o terceiro período da minha graduação tive uma matéria chamada Programação Funcional (ou PF), nela estudamos o paradígma de programação funcional, que é "apenas" uma classificação das linguagens de programação como existem os paradigmas Orientado a Objetos (POO) e Procedimental, ou seja, é a forma como se programa em tal linguagem. Nessa disciplina usamos a linguagem Haskell e nela vimos algumas funções que se utilizam para fazer determinadas ações e são essas funções que trago para vocês. Mas ao invés de trazê-las em Haskell, como eu as aprendi inicialmente, vou trazê-las em uma das linguagens mais populares do momento (e porquê não, a melhor 😬), que é o Python.

O Python é majoritariamente uma linguagem orientada a objetos, mas ela também é multiparadigma e suporta a programação funcional e contêm as funções mencionadas.

As funções que irei trazer são map, filter, reduce e zip. De bônus também irei mostrar como se monta uma lista e um dicionário por compreensão, que também são formas de construir essas estruturas de dados de uma forma mais funcional. Então bora lá.

## Função `map`
A função `map` recebe dois parâmetros de entrada. O primeiro uma função que você quer aplicar nos elementos e o segundo uma sequência com os elementos (pode ser uma lista, tupla, etc). A função `map` aplica a função de entrada em cada valor da sequência passada e retorna uma sequência com os valores retornados da função. Confuso? Nada, é muito mais simples do que parece, vamos pro código:
```python
# primeiro vamos criar nossa sequência (que pode ser uma lista ou tupla)
sequencia = [1, 2, 3]

# agora vamos criar uma função que retorna o dobro do valor de entrada
def funcao_dobro(valor):
  return 2 * valor
  
# basta agora aplicar a função map na função dobro junto com a sequencia e podemos ver o resultado
resultado = map(funcao_dobro, sequencia)
resultado = list(resultado)
print(f'Nossa lista de saída é: {resultado}')
```
![Saída da Função map](https://raw.githubusercontent.com/johnsigma/meuPortifolio/master/funcoes_funcionais/map_saida.png)

Viu como é simples usar a `map`? Ela pegou cada elemento da nossa lista (que poderia ser uma tupla também) e aplicou a função passada (nesse caso a função dobro). Importante lembrar que a função `map()` retorna um objeto iterável do tipo `map`, por isso devemos converter o retorno dela para uma estrutura de sequência (seja uma lista ou tupla), por isso usamos `resultado = list(resultado)`.

## Função `filter`
A função `filter` recebe dois parâmetros de entrada. Assim como na `map` o primeiro é uma função que você quer aplicar nos elementos e o segundo uma sequência com os elementos. Diferente da função `map`, na função `filter` devemos passar uma função que retorna um valor booleano (True ou False) e a função `filter` vai aplicar essa função em cada valor da sequência passada e vai retornar uma sequência apenas com os valores que retornaram True (verdadeiro) da função passada. Como seu próprio nome diz: ela filtra os valores passados de acordo com uma função. Para não restar dúvidas bora pro código:
```python
# primeiro vamos criar nossa sequência, dessa vez uma tupla apenas para mostrar que essas função podem ser aplicadas a listas e tuplas
sequencia = ('Pato', 'Cadeira', 'Ciência', 'Bola', 'Cobra')

# agora vamos criar uma função que retorna um valor Booleano, nossa função vai retornar True (verdadeiro) se a palavra tiver 5 ou mais letras
def funcao_letras(palavra):
  if len(palavra) >= 5:
    return True
    
# vamos aplicar a função filter na nossa função e sequência e exibir o resultado
resultado = filter(funcao_letras, sequencia)
resultado = tuple(resultado)
print(f'Nossa tupla de saída é: {resultado}')
```
![Saída da Função filter](https://github.com/johnsigma/meuPortifolio/blob/master/funcoes_funcionais/filter_saida.png?raw=true)

Perceba que utilizei uma tupla e ao invés de usar valores numéricos utilizei Strings (palavras), fiz isso apenas para dar mais exemplos de como utilizar essas funções, você pode utilizar listas e valores numéricos na função `filter` (assim como na `map`).

Perceba o que a `filter` fez, ela aplicou a função `funcao_letras` nas palavras (Strings) da sequência e só retornou as palavras que retornaram como verdadeiro (True) da função passada. Em outras palavras, ela retornou apenas aquelas palavras que continham 5 ou mais letras. Fácil não é? Não esqueça que assim como a função `map` a função `filter` retorna um objeto iterável do tipo filter e devemos converter o retorno da função para uma estrutura de sequência (uma lista ou tupla).

## Função `reduce`
A função `reduce` tem uma característica diferente das outras funções vistas aqui, ela não é uma função built-in do Python. Ou seja, ela não vem pronta pra ser utilizada como as outras, sendo necessário importá-la para podermos usá-la. Mas não se preocupe, pois importar módulo (pacotes, bibliotecas) em Python é muito simples e vamos fazer isso com apenas uma linha de código. A função `reduce` pertence ao módulo `functools`, para saber mais sobre esse módulo [clique aqui](https://docs.python.org/3/library/functools.html).

A função `reduce` recebe dois (ou três) parâmetros de entrada. O primeiro é uma função que será aplicada aos elementos da sequência e o segundo é a própria sequência. O terceiro parâmetro pode ser usado para definir um valor inicial, mas ele é totalmente opcional. A função `reduce` deve receber uma função que espera dois argumentos e retorna apenas um valor. A `reduce` então pega os dois primeiros valores da nossa sequência e aplica neles nossa função de entrada e retorna um valor de saída, então a `reduce` pega esse valor retornado e o próximo valor da nossa sequência que não foi utilizado e aplica novamente nossa função de entrada nesses valores até que nossa sequência termine e a `reduce` retorna o valor de saída. No caso de passarmos um inicializador (que pode também ser uma sequência ou apenas um valor) como parâmetro da `reduce` então nossa `reduce` irá aplicar primeiramente a função de entrada nos valores (ou valor) de inicialização. Parace bem complicada na explicação, mas seu funcionamento é bem simples. Bora lá:

```python
# primeiro, como dito anteriormente, devemos importar a função reduce do módulo funtools para utilizá-la
from functools import reduce

# criando nossa sequência
lista = [1, 8, 7, 14]

# agora vamos criar nossa função de entrada, ela recebe dois valores e retorna o maior entre eles
def maior(valor_a, valor_b):
  if valor_a >= valor_b:
    return valor_a
    
  return valor_b
  
# vamos aplicar a reduce na nossa função e sequência
resultado = reduce(maior, lista)
print(f'O maior valor da nossa sequência é: {resultado}')

# aplicando a reduce na nossa função, sequência mas passando um inicializador
resultado = reduce(maior, lista, 25)
print(f'O maior valor da nossa sequência é: {resultado}')
```
![Saída da Função reduce](https://github.com/johnsigma/meuPortifolio/blob/master/funcoes_funcionais/reduce_saida.png?raw=true)

Bastante simples né!? Na nossa primeira saída a `reduce` aplicou a função `maior` nos valores da nossa sequência, primeiro ela pega os valores 1 e 8 e aplica na nossa `maior`, nossa função retorna o 8 por ele ser `maior` que o 1, após isso a `reduce` aplica a maior no 8 e no 7 que retorna o 8, por último se aplica a `maior` no 8 e 14 que retorna 14, como não há mais valores na nossa sequência a `reduce` retorna o valor 14.

Percebe que quando nós passamos um inicializador como parâmetro a `reduce` o considera e aplica a função de entrada nele primeiramente. Então no nosso segundo exemplo a `reduce`  aplica a `maior` no 25 e no 1 e depois sucessivamente até retornar o maior valor comparado pela `maior` que é o própio inicializador (mas o retorno poderia não ser ele necessariamente).
