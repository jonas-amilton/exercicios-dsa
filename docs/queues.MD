# Filas (Queues) --- Operações e Análise de Complexidade

Filas são estruturas de dados que seguem o princípio **FIFO** (First In,
First Out): o primeiro elemento inserido é o primeiro a ser removido.
São implementadas tipicamente com linked lists ou arrays circulares, e
aparecem em cenários como escalonamento de tarefas, BFS em grafos e
sistemas de mensageria.

------------------------------------------------------------------------

## Tabela de Complexidade

  ---------------------------------------------------------------------------------
  Operação                Complexidade de Tempo        Observações Técnicas
  ----------------------- ---------------------------- ----------------------------
  Enqueue (inserção)      O(1)                         Inserção sempre ocorre no
                                                       final da fila

  Dequeue (remoção)       O(1)                         Remoção sempre ocorre no
                                                       início da fila

  Peek / Front            O(1)                         Leitura do elemento na
                                                       frente sem remover

  Busca por valor         O(n)                         Filas não oferecem acesso
                                                       direto por posição

  Verificação de vazio    O(1)                         Checar se `head == null`
                                                       ou `size == 0`
  ---------------------------------------------------------------------------------

------------------------------------------------------------------------

## Complexidade de Espaço

-   Espaço ocupado pelos elementos armazenados: **O(n)**
-   Implementação com linked list: overhead de ponteiro por nó
-   Implementação com array circular: tamanho fixo ou redimensionamento
    amortizado O(n)

------------------------------------------------------------------------

## Exercícios Comentados

### Exercício 1 --- BFS em Grafo

Realize a busca em largura (Breadth-First Search) a partir de um nó
origem em um grafo representado por lista de adjacência.

**Abordagem com Fila:**

1.  Inicializar a fila com o nó de origem e marcá-lo como visitado.
2.  Enquanto a fila não estiver vazia: remover o elemento da frente,
    processar o nó e enfileirar todos os seus vizinhos não visitados.

-   Complexidade de tempo: **O(V + E)** — V vértices, E arestas
-   Complexidade de espaço: **O(V)** — fila pode conter todos os vértices

A fila garante que os nós sejam processados na ordem correta por nível,
característica fundamental do BFS.

------------------------------------------------------------------------

### Exercício 2 --- Implementar Fila com Duas Pilhas

Simule o comportamento de uma fila utilizando apenas duas pilhas.

#### Abordagem Amortizada

Manter duas pilhas: `stack_in` (para enqueue) e `stack_out` (para
dequeue).

-   **Enqueue:** empilhar em `stack_in` → O(1)
-   **Dequeue:** se `stack_out` estiver vazia, transferir todos os
    elementos de `stack_in` para `stack_out`; então desempilhar de
    `stack_out`.

Análise amortizada:

-   Complexidade de tempo por operação: **O(1) amortizado**
-   Complexidade de espaço: **O(n)**

Cada elemento é movido no máximo uma vez entre as pilhas, garantindo
custo amortizado constante.

------------------------------------------------------------------------

## Padrões de Raciocínio

Alguns padrões recorrentes em problemas com filas:

-   **Processamento em ordem de chegada → FIFO é a estrutura natural**
-   **BFS em grafos ou árvores → fila garante exploração por níveis**
-   **Sliding window com remoção nas bordas → deque (fila dupla)**
-   **Simulação de filas com restrições → duas pilhas ou fila circular**

A fila é ideal quando a ordem de processamento deve preservar a
sequência de entrada.\
Para cenários que exigem acesso ao menor ou maior elemento, considere
uma fila de prioridade (heap).\
Quando remoções precisam ocorrer em ambas as extremidades, a estrutura
adequada é o deque (double-ended queue).
