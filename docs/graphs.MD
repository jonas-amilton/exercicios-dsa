 # Graphs --- Operações e Análise de Complexidade

Graphs (grafos) são estruturas que modelam relações entre pares de
objetos (vértices/nós) ligadas por arestas (edges). Grafos podem ser
direcionados ou não, ponderados ou não, e aparecem em redes, mapas,
dependências de tarefas, recomendações e muitos outros problemas.

------------------------------------------------------------------------

## Tabela de Complexidade

  ---------------------------------------------------------------------------------------------
  Operação / Algoritmo            Complexidade de Tempo        Observações Técnicas
  ------------------------------- ---------------------------- -------------------------------
  BFS / DFS (travessia)          O(V + E)                     Visita cada vértice e aresta uma vez

  Verificar aresta (adjMatrix)   O(1)                         Teste direto em matriz de adjacência

  Iterar vizinhos (adjList)      O(deg(v))                    Proporcional ao grau do vértice

  Dijkstra (heap)                O(E log V)                   Para pesos não-negativos

  Bellman-Ford                   O(V * E)                     Suporta arestas com peso negativo

  Topological sort (Kahn/DFS)    O(V + E)                     Apenas em DAGs (grafo acíclico)

  Kruskal (MST)                  O(E log E) ~ O(E log V)      Ordena arestas + union-find

  Prim (heap)                    O(E log V)                   Alternativa para MST (dense/sparse)

  Encontrar componentes conectadas O(V + E)                   DFS/BFS em grafos não direcionados
  ---------------------------------------------------------------------------------------------

------------------------------------------------------------------------

## Complexidade de Espaço

- Adjacency list: **O(V + E)**
- Adjacency matrix: **O(V²)**
- Estruturas auxiliares (fila/stack/heap): até **O(V)** ou **O(E)**

------------------------------------------------------------------------

## Representações (quando escolher)

- **Adjacency list:** ideal para grafos esparsos, iteração eficiente
  sobre vizinhos.
- **Adjacency matrix:** útil para grafos densos ou quando precisar
  checar existência de aresta em O(1).
- **Edge list:** prática para algoritmos que processam arestas (Kruskal).

------------------------------------------------------------------------

## Exercícios Comentados

### Exercício 1 --- Menor caminho em grafo não ponderado

Use BFS a partir da fonte para obter distâncias mínimas (em número de
arestas) a todos os vértices.

- Complexidade de tempo: **O(V + E)**
- Complexidade de espaço: **O(V)**

------------------------------------------------------------------------

### Exercício 2 --- Menor caminho com pesos não-negativos (Dijkstra)

Utilize fila de prioridade (heap) para relaxar arestas. Para grafos
densos, estruturas alternativas podem ser melhores; para grafos com
pesos negativos, use Bellman-Ford.

- Complexidade de tempo (heap binário): **O(E log V)**
- Complexidade de espaço: **O(V + E)**

------------------------------------------------------------------------

### Exercício 3 --- MST (Kruskal / Prim)

Kruskal: ordenar arestas e usar union-find para evitar ciclos. Prim:
começar de um vértice e crescer a árvore usando uma heap.

- Complexidade (Kruskal): **O(E log E)**
- Complexidade (Prim com heap): **O(E log V)**

------------------------------------------------------------------------

### Exercício 4 --- Detectar ciclo em grafo direcionado

Use DFS mantendo um conjunto/flag de recursão (stack) para detectar
arestas de retorno; em alternativa, tente a ordenação topológica — se
falhar, existe ciclo.

- Complexidade de tempo: **O(V + E)**

------------------------------------------------------------------------

## Padrões de Raciocínio

- **BFS →** caminhos mínimos em grafos não ponderados, níveis/alcance
- **Dijkstra →** caminhos mínimos com pesos não-negativos (heap)
- **Bellman-Ford →** permite pesos negativos; detecta ciclos negativos
- **Union-Find →** conectividade, Kruskal, componentes dinâmicas
- **Topological sort →** ordem linear em DAGs (dependências, build)
- **DFS recursivo vs iterativo →** escolha conforme limite de recursão
- **Converter problema para grafo →** mapeie estados para nós e
  transições para arestas (problemas de busca/DP em grafos)

Para problemas de otimização em grafos, pense primeiro na representação
(lista vs matriz) e na densidade do grafo (sparse vs dense) — isso
guia a escolha do algoritmo e da estrutura auxiliar.
