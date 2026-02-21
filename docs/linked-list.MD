# Linked Lists --- Operações e Análise de Complexidade

Linked Lists são estruturas de dados compostas por nós encadeados, onde
cada nó armazena um valor e um ponteiro para o próximo elemento. Ao
contrário dos arrays, os elementos não ocupam posições contíguas na
memória, o que torna inserções e remoções nas extremidades eficientes,
mas impõe custo linear para acesso por posição.

------------------------------------------------------------------------

## Tabela de Complexidade

  ---------------------------------------------------------------------------------
  Operação                Complexidade de Tempo        Observações Técnicas
  ----------------------- ---------------------------- ----------------------------
  Acesso por índice       O(n)                         Requer percorrer a lista
                                                       desde o início

  Busca por valor         O(n)                         Percorre sequencialmente até
                                                       encontrar

  Inserção no início      O(1)                         Apenas reatribui o ponteiro
                                                       `head`

  Inserção no final       O(1) com tail / O(n) sem     Depende de haver ponteiro
                                                       para a cauda

  Inserção em posição     O(n)                         Necessário percorrer até o
  arbitrária                                           nó anterior

  Remoção no início       O(1)                         Reatribui `head` para o
                                                       próximo nó

  Remoção no final        O(n) em SLL / O(1) em DLL    Lista duplamente encadeada
                                                       mantém ponteiro `prev`

  Remoção por valor       O(n)                         Necessário localizar e
                                                       reatribuir ponteiros
  ---------------------------------------------------------------------------------

------------------------------------------------------------------------

## Complexidade de Espaço

-   Espaço principal ocupado pelos nós: **O(n)**
-   Cada nó carrega overhead de ponteiro(s): O(1) adicional por nó
-   Em listas duplamente encadeadas (DLL): dois ponteiros por nó (`next`
    e `prev`)

------------------------------------------------------------------------

## Exercícios Comentados

### Exercício 1 --- Inversão de Lista

Inverta uma linked list sem utilizar estrutura auxiliar.

**Abordagem Iterativa:**

Manter três ponteiros: `prev`, `curr` e `next`. A cada iteração,
redirecionar `curr.next` para `prev`, avançar os três ponteiros e repetir
até o fim da lista.

-   Complexidade de tempo: **O(n)**
-   Complexidade de espaço: **O(1)**

**Abordagem Recursiva:**

Recursar até o último nó, retornando-o como nova `head`. Na volta da
recursão, reatribuir os ponteiros em ordem reversa.

-   Complexidade de tempo: **O(n)**
-   Complexidade de espaço: **O(n)** — uso da pilha de chamadas

------------------------------------------------------------------------

### Exercício 2 --- Detecção de Ciclo

Dado uma linked list, determine se ela contém um ciclo.

#### Abordagem Ingênua

Armazenar todos os nós visitados em um conjunto (hash set) e verificar
se o nó atual já foi visto:

-   Complexidade de tempo: **O(n)**
-   Complexidade de espaço: **O(n)**

#### Abordagem Otimizada --- Algoritmo de Floyd

Utilizar dois ponteiros: `slow` (avança 1 nó) e `fast` (avança 2 nós).
Se existir ciclo, os ponteiros necessariamente se encontrarão.

-   Complexidade de tempo: **O(n)**
-   Complexidade de espaço: **O(1)**

Essa técnica elimina o custo de memória sem aumentar o custo de tempo.

------------------------------------------------------------------------

## Padrões de Raciocínio

Alguns padrões recorrentes em problemas com linked lists:

-   **Dois ponteiros (slow/fast) → detecção de ciclo, ponto médio**
-   **Percurso com ponteiro anterior → remoção segura de nós**
-   **Uso de nó sentinela (dummy head) → simplifica inserção/remoção na borda**
-   **Recursão → inversão, merge de listas ordenadas**

A escolha entre lista simples e duplamente encadeada depende da
frequência de remoções na cauda.\
Se inserções e remoções ocorrem majoritariamente nas extremidades, linked
lists superam arrays.\
Se há muitas buscas por índice, arrays são a escolha mais eficiente.
