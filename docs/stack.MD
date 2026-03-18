# Stacks --- Operações e Análise de Complexidade

Stacks (pilhas) são estruturas de dados que seguem o princípio LIFO
(Last In, First Out): o último elemento inserido é o primeiro a ser
removido. São úteis para rastrear chamadas de função, desfazer/refazer
operações, travessias em profundidade e avaliação de expressões.

------------------------------------------------------------------------

## Tabela de Complexidade

	-----------------------------------------------------------------------------
	Operação                Complexidade de Tempo        Observações Técnicas
	----------------------- ---------------------------- ----------------------------
	Push (inserir)          O(1)                         Inserção no topo da pilha

	Pop (remover)           O(1)                         Remoção do topo da pilha

	Peek / Top              O(1)                         Acessa o elemento do topo

	Busca por valor         O(n)                         Percorre todos os elementos

	Inserção em posição     O(n)                         Requer deslocamento até a
	arbitrária                                             posição (não comum)
	-----------------------------------------------------------------------------

------------------------------------------------------------------------

## Complexidade de Espaço

- Espaço principal ocupado pela pilha: **O(n)**
- Overhead depende da implementação (array dinâmico vs lista ligada)

------------------------------------------------------------------------

## Exercícios Comentados

### Exercício 1 --- Validação de Parênteses

Dada uma string contendo apenas os caracteres '(', ')', '{', '}', '[' e
']', determine se a string está com os parênteses balanceados.

**Abordagem:**

- Percorrer a string empilhando os parênteses de abertura.
- Ao encontrar um parêntese de fechamento, verificar se o topo da pilha
	corresponde ao tipo esperado; se não, a string é inválida.
- Ao final, a pilha deve estar vazia para a string ser válida.

- Complexidade de tempo: **O(n)**
- Complexidade de espaço: **O(n)**

------------------------------------------------------------------------

### Exercício 2 --- Ordenar uma pilha com outra pilha (sem usar arrays)

Ordenar uma pilha (topo menor ou maior) usando apenas outra pilha
auxiliar e operações de pilha.

**Abordagem (iterativa):**

- Usar uma pilha auxiliar para manter os elementos em ordem parcial.
- Repetidamente remover o topo da pilha original e inserir na pilha
	auxiliar na posição correta (desempilhando de/para ajustar ordem).

- Complexidade de tempo: **O(n²)** no pior caso (comparações e deslocamentos)
- Complexidade de espaço: **O(n)** (pilha auxiliar)

------------------------------------------------------------------------

## Padrões de Raciocínio

- **LIFO →** útil para desfazer ações, rastrear chamadas recursivas
- **Pilha auxiliar →** reverte ordem, auxilia em algoritmos de ordenação
- **Monotonic Stack →** resolver problemas de "next greater/smaller"
	em O(n)
- **Stack para DFS →** simula recursão quando necessário ou evita
	limites de profundidade da pilha de chamadas

A escolha entre implementar uma pilha com array dinâmico ou lista
ligada depende de requisitos de memória e da necessidade de crescimento
dinâmico sem realocações frequentes.

