# Binary Trees --- Operações e Análise de Complexidade

Binary Trees (árvores binárias) são estruturas hierárquicas onde cada
nó pode ter no máximo dois filhos — comumente chamados de `left` e
`right`. Árvores binárias servem como base para diversas estruturas
mais especializadas (BST, AVL, Red-Black, heaps) e são fundamentais em
algoritmos de busca, ordenação e indexação.

------------------------------------------------------------------------

## Tabela de Complexidade

	---------------------------------------------------------------------------------
	Operação                    Complexidade de Tempo        Observações Técnicas
	--------------------------- ---------------------------- ----------------------------
	Busca / Inserção / Remoção  O(h)                         Depende da altura `h` da árvore

	Busca / Inserção em BST     O(h)                         Em árvore balanceada,
	(média)                                                  `h = O(log n)`

	Busca / Inserção em BST     O(n)                         Caso degenerado (lista
	(pior caso)                                              encadeada) quando desbalanceada

	Travessia (in/pre/post)     O(n)                         Visita todos os nós

	Traversal level-order       O(n)                         Utiliza fila (BFS)

	Cálculo da altura           O(n)                         Percorre a árvore inteira
	---------------------------------------------------------------------------------

------------------------------------------------------------------------

## Complexidade de Espaço

- Espaço principal ocupado pela árvore: **O(n)**
- Espaço extra para recursão: **O(h)** (pilha de chamadas)
- Estruturas auxiliares (fila para BFS): **O(n)** no pior caso

------------------------------------------------------------------------

## Exercícios Comentados

### Exercício 1 --- Travessias (Inorder, Preorder, Postorder)

Implemente as três travessias clássicas e explique quando cada uma é útil.

**Abordagem Recursiva (exemplo: inorder):**

- Chamar `inorder(left)`
- Processar `root` (visitar)
- Chamar `inorder(right)`

- Complexidade de tempo: **O(n)**
- Complexidade de espaço: **O(h)** (recursão)

------------------------------------------------------------------------

### Exercício 2 --- Verificar se é Binary Search Tree (BST)

Dada uma binary tree, verificar se ela satisfaz a propriedade BST
(left < root < right).

**Abordagem (limites):**

- Fazer uma travessia DFS mantendo um intervalo válido (min, max) para
	cada nó; verificar que o valor do nó está dentro do intervalo.

- Complexidade de tempo: **O(n)**
- Complexidade de espaço: **O(h)**

------------------------------------------------------------------------

### Exercício 3 --- Lowest Common Ancestor (LCA)

Encontrar o menor ancestral comum de dois nós em uma BST ou em uma
árvore binária genérica.

**Abordagem em BST:**

- Percorrer a partir da raiz: se ambos os valores são menores que a
	raiz, ir para a esquerda; se ambos são maiores, ir para a direita;
	caso contrário, a raiz atual é o LCA.

- Complexidade de tempo: **O(h)**

**Abordagem em árvore genérica:**

- Percorrer recursivamente; um nó é LCA se dois de seus subárvores
	contêm os nós buscados.

- Complexidade de tempo: **O(n)**

------------------------------------------------------------------------

## Padrões de Raciocínio

- **Recursão / Divide and Conquer →** a maioria dos problemas em
	árvores são resolvidos dividindo o problema nos subárvores
- **DFS (recursivo ou stack) vs BFS (fila) →** escolha conforme
	objetivo: DFS para inspeção de caminhos; BFS para níveis/altura
- **Manter limites (min/max) →** verificação de BST
- **Conversões entre estruturas →** usar pilha/filas para iterativo
	ou para evitar recursão

Para problemas que exigem altura ou distância, pense em postorder
para agregar resultados das subárvores antes de calcular o valor do
nó atual.

