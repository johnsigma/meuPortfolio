# Funções "Funcionais" em Python
Olá a todos, meu nome é John Cunha e sou estudante de Graduação em Ciência da Computação. Este é meu primeiro artigo escrito no Medium, então dêem uma relevada sobre a qualidade, prometo que vou tentar melhorar daqui pra frente 😁.

Como sou estudante de Computação nada mais lógico que trazer esse tema no artigo, mas calma que não irei começar a despejar teoria aqui. Como o título do artigo sugere, hoje irei trazer para vocês funções "funcionais" em Python e como utilizá-las, então vem comigo.

## Primeiro, o que são funções "funcionais"?
Primeiro, o que são funções "funcionais"? Durante o terceiro período da minha graduação tive uma matéria chamada Programação Funcional (ou PF), nela estudamos o paradígma de programação funcional, que é "apenas" uma classificação das linguagens de programação como existem os paradigmas Orientado a Objetos (POO) e Procedimental, ou seja, é a forma como se programa em tal linguagem. Nessa disciplina usamos a linguagem Haskell e nela vimos algumas funções que se utilizam para fazer determinadas ações e são essas funções que trago para vocês. Mas ao invés de trazê-las em Haskell, como eu as aprendi inicialmente, vou trazê-las em uma das linguagens mais populares do momento (e porquê não a melhor 😬), que é o Python.

O Python é majoritariamente uma linguagem orientada a objetos, mas ela também é multiparadigma e suporta a programação funcional e contêm as funções mencionadas.

As funções que irei trazer são map, filter, reduce e zip. De bônus também irei mostrar como se montar uma lista e um dicionário por compreensão, que também são formas de construir essas estruturas de dados de uma forma mais funcional. Então bora lá.

## Função `map()`
A função `map()` recebe dois parâmetros de entrada. O primeiro uma função que você quer aplicar nos elementos e o segundo uma sequência com os elementos (pode ser uma lista, tupla, etc). A função `map()` aplica a função de entrada em cada posição da sequência passada. Confuso? Nada, é muito mais simples do que parece, vamos pro código:
```python
# primeiro vamos criar nossa sequência (que pode ser uma lista ou tupla)
sequencia = [1, 2, 3]

# agora vamos criar uma função que retorna o dobro do valor de entrada
def funcao_dobro(valor):
  return 2 * valor
  
# basta agora aplicar a função map na função dobro junto com a sequencia e podemos ver o resultado
resultado = map(funcao_dobro, sequencia)
print(f'Nossa lista de saída é: {resultado}')
```
![Saída da Função map](https://raw.githubusercontent.com/johnsigma/meuPortifolio/master/funcoes_funcionais/map_saida.png)
