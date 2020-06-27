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
