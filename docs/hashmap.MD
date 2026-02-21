# Hash Maps --- Operações e Análise de Complexidade

Hash Maps (ou tabelas hash) são estruturas de dados que associam chaves
a valores por meio de uma função de hash. A função transforma a chave em
um índice do array interno, permitindo acesso, inserção e remoção em
tempo constante médio. Colisões são tratadas por encadeamento (chaining)
ou endereçamento aberto (open addressing).

------------------------------------------------------------------------

## Tabela de Complexidade

  ---------------------------------------------------------------------------------
  Operação                Complexidade de Tempo        Observações Técnicas
  ----------------------- ---------------------------- ----------------------------
  Inserção                O(1) médio / O(n) pior       Pior caso ocorre com muitas
                                                       colisões na mesma posição

  Busca por chave         O(1) médio / O(n) pior       Depende da qualidade da
                                                       função de hash

  Remoção por chave       O(1) médio / O(n) pior       Mesmas condições da busca

  Iteração sobre pares    O(n)                         Percorre todas as entradas
                                                       da tabela

  Verificação de chave    O(1) médio                   Equivalente a uma busca
  (`contains`)
  ---------------------------------------------------------------------------------

------------------------------------------------------------------------

## Complexidade de Espaço

-   Espaço ocupado pelas entradas armazenadas: **O(n)**
-   Array interno pode ter capacidade maior que n (fator de carga
    controla a proporção)
-   Rehashing: O(n) tempo e espaço quando o fator de carga é excedido

------------------------------------------------------------------------

## Exercícios Comentados

### Exercício 1 --- Contagem de Frequência

Dado um array de elementos, conte quantas vezes cada elemento aparece.

**Abordagem com Hash Map:**

Percorrer o array uma única vez. Para cada elemento, incrementar seu
contador no mapa (inicializando em 1 caso ainda não exista).

-   Complexidade de tempo: **O(n)**
-   Complexidade de espaço: **O(n)** — no pior caso, todos os elementos
    são distintos

Sem hash map, a abordagem ingênua exigiria dois loops aninhados: O(n²)
de tempo e O(1) de espaço.

------------------------------------------------------------------------

### Exercício 2 --- Dois Números com Soma Alvo

Dado um array e um valor alvo `T`, encontre dois índices cujos elementos
somam exatamente `T`.

#### Abordagem Ingênua

Dois loops aninhados testando todos os pares:

-   Complexidade de tempo: **O(n²)**
-   Complexidade de espaço: **O(1)**

#### Abordagem Otimizada

Percorrer o array uma única vez, armazenando cada elemento e seu índice
no mapa. Para cada elemento `x`, verificar se `(T - x)` já está
presente:

1.  Calcular o complemento `c = T - x`.
2.  Se `c` estiver no mapa, retornar os dois índices.
3.  Caso contrário, inserir `x` com seu índice no mapa.

-   Complexidade de tempo: **O(n)**
-   Complexidade de espaço: **O(n)**

A verificação de existência no mapa ocorre em tempo constante médio,
reduzindo o problema de O(n²) para O(n).

------------------------------------------------------------------------

## Padrões de Raciocínio

Alguns padrões recorrentes em problemas com hash maps:

-   **Contagem/frequência de elementos → mapa de `elemento → contagem`**
-   **Verificação de existência em O(1) → substituir busca linear por lookup no mapa**
-   **Agrupamento por critério → mapa de `critério → lista de elementos`**
-   **Complemento aritmético → armazenar vistos e checar `T - x` a cada passo**

Hash maps trocam espaço por tempo: quase sempre transformam soluções
O(n²) em O(n).\
A qualidade da função de hash é crítica; funções ruins aumentam
colisões e degradam o desempenho para O(n) no pior caso.\
Para dados ordenados ou buscas por intervalo, árvores balanceadas (BST)
são mais adequadas que hash maps.
