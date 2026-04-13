# B-Trees --- Operações e Análise de Complexidade

B-Trees são árvores de busca balanceadas, amplamente usadas em bancos de
dados e sistemas de arquivos. Diferente de uma binary search tree, cada
nó pode armazenar várias chaves e ter vários filhos. Isso reduz a altura
da árvore e minimiza acessos a disco, que costumam ser o gargalo nesses
ambientes.

------------------------------------------------------------------------

## Propriedades Principais

- Cada nó armazena várias chaves em ordem crescente.
- Um nó interno com `k` chaves possui `k + 1` filhos.
- Todas as folhas ficam no mesmo nível.
- A árvore permanece balanceada por meio de split e merge de nós.
- Em uma B-Tree de grau mínimo `t`:
  - cada nó, exceto a raiz, possui entre `t - 1` e `2t - 1` chaves;
  - cada nó interno, exceto a raiz, possui entre `t` e `2t` filhos.

------------------------------------------------------------------------

## Tabela de Complexidade

  ---------------------------------------------------------------------------------
  Operação                    Complexidade de Tempo        Observações Técnicas
  --------------------------- ---------------------------- ----------------------------
  Busca                      O(log n)                     Mais precisamente O(log_t n)

  Inserção                   O(log n)                     Pode exigir split de nós

  Remoção                    O(log n)                     Pode exigir borrow/merge

  Percurso em ordem          O(n)                         Visita todas as chaves

  Consulta por intervalo     O(log n + k)                 k = quantidade de chaves retornadas

  Acesso à altura            O(1)                         A altura é pequena e balanceada
  ---------------------------------------------------------------------------------

------------------------------------------------------------------------

## Complexidade de Espaço

- Espaço ocupado pelas chaves e ponteiros: **O(n)**
- Overhead por nó depende do grau mínimo `t` e da implementação
- Em sistemas de armazenamento, o tamanho do nó costuma ser ajustado ao
  tamanho da página/bloco de disco

------------------------------------------------------------------------

## Inserção e Balanceamento

Quando um nó fica cheio, ele é dividido em dois nós e a chave mediana é
promovida para o pai. Esse processo mantém a árvore balanceada e evita
que a altura cresça rapidamente.

Na remoção, se um nó ficar com poucas chaves, a estrutura pode pegar uma
chave emprestada de um irmão (borrow/redistribution) ou fundir nós
adjacentes (merge).

------------------------------------------------------------------------

## Exercícios Comentados

### Exercício 1 --- Buscar uma chave

Dada uma chave, localizar sua posição na árvore.

**Abordagem:**

- Comparar a chave com as chaves do nó atual.
- Descer para o filho apropriado até encontrar a chave ou chegar a uma
  folha.

- Complexidade de tempo: **O(log n)**

------------------------------------------------------------------------

### Exercício 2 --- Inserir uma chave

Inserir uma nova chave sem violar as propriedades da B-Tree.

**Abordagem:**

- Descer até a folha correta.
- Inserir a chave em ordem.
- Se houver overflow, dividir o nó e promover a mediana.

- Complexidade de tempo: **O(log n)**

------------------------------------------------------------------------

### Exercício 3 --- Consulta por intervalo

Retorne todas as chaves entre `L` e `R`.

**Abordagem:**

- Localizar o primeiro nó relevante com busca logarítmica.
- Percorrer as chaves em ordem, coletando apenas as que caem no
  intervalo.

- Complexidade de tempo: **O(log n + k)**

------------------------------------------------------------------------

### Exercício 4 --- Comparar B-Tree com BST

Explique por que B-Trees são preferidas em banco de dados, enquanto BSTs
simples são menos usadas para armazenamento em bloco.

**Resposta resumida:**

- B-Trees têm maior fator de ramificação, reduzindo a altura.
- Menor altura significa menos leituras de disco ou páginas.
- BSTs podem ficar muito altas se não forem balanceadas e fazem mais
  acessos.

------------------------------------------------------------------------

## Padrões de Raciocínio

- **Grande fator de ramificação →** reduz altura e melhora acesso em
  disco
- **Split na inserção →** mantém limites de ocupação dos nós
- **Borrow/merge na remoção →** corrige underflow sem perder balanceamento
- **Consulta por intervalo →** aproveitar a ordenação interna das chaves
- **Escolha do grau mínimo `t` →** ajusta desempenho entre altura e
  custo por nó

B-Trees são a escolha clássica quando o custo de acesso a disco domina.
Em memória principal, árvores balanceadas binárias podem ser mais
simples; em armazenamento secundário, o grande fan-out da B-Tree faz a
diferença.
