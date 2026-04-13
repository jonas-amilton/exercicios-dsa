# Tries (Prefix Trees) --- Operações e Análise de Complexidade

Tries (árvores de prefixo) são estruturas em árvore especializadas para
armazenar coleções de strings de forma eficiente quando há consultas por
prefixo. Cada aresta representa um caractere; cada nó representa o
prefixo formado pelo caminho da raiz até aquele nó.

------------------------------------------------------------------------

## Tabela de Complexidade

  -------------------------------------------------------------------------------
  Operação                       Complexidade de Tempo       Observações Técnicas
  ------------------------------ --------------------------- -----------------------------
  Busca (exata)                  O(L)                        L = comprimento da chave

  Inserção                       O(L)                        Insere/percorrer L nós

  Remoção                        O(L)                        Remove e possivelmente elimina
                                                         nós órfãos

  Consulta por prefixo           O(L + R)                    L = comprimento do prefixo,
                                                         R = tamanho da saída (número de
                                                         palavras retornadas)

  Autocomplete (k sugestões)     O(L + k)                    Encontrar nó do prefixo +
                                                         coletar k resultados

  Construir a partir de N palavras O(total_chars)            Soma dos comprimentos de todas
                                                         as palavras
  -------------------------------------------------------------------------------

------------------------------------------------------------------------

## Complexidade de Espaço

- Cada nó contém ponteiros (ou mapeamento) para filhos: em um array
  fixo por alfabeto o custo por nó é **O(Σ)** (Σ = tamanho do alfabeto).
- Em representações com dicionário/hash por nó, o custo é **O(total
  characters)** (próximo ao número total de arcos criados).
- Tries podem consumir muita memória; técnicas como *compressed tries*
  (radix trees) e armazenamento compacto mitigam isso.

------------------------------------------------------------------------

## Exercícios Comentados

### Exercício 1 — Implementar Trie básico

Implemente `insert(word)`, `search(word)` e `startsWith(prefix)`.

**Abordagem:** usar nós com mapa `children` e boolean `isWord`.

- Complexidade de tempo (cada operação): **O(L)**
- Complexidade de espaço: **O(total_chars)** para construir a trie

------------------------------------------------------------------------

### Exercício 2 — Longest Common Prefix

Dado um array de strings, encontre o maior prefixo comum usando trie.

**Abordagem:** construir a trie com todas as palavras e andar da raiz
até o primeiro nó que tenha mais de um filho ou marque fim de palavra.

- Complexidade de tempo: **O(total_chars)**

------------------------------------------------------------------------

### Exercício 3 — Autocomplete com frequência (top-k)

Armazene em cada nó contadores/frequências ou uma lista ordenada para
suporte a sugestões por relevância.

**Abordagem:** após localizar o nó do prefixo (O(L)), fazer uma busca
heurística (DFS/BFS) para coletar até `k` termos mais relevantes.

- Complexidade de tempo: **O(L + k log m)** (dependendo da estratégia
  de ordenação), ou **O(L + k)** em implementações otimizadas

------------------------------------------------------------------------

### Exercício 4 — Compressed Trie / Radix Tree

Reduz o número de nós ao agrupar caminhos onde há um único filho.

**Vantagem:** menor uso de memória e menos overhead de ponteiros;
**Cuidado:** operações de manipulação de arestas exigem operações em
strings (substrings) em vez de caracteres únicos.

------------------------------------------------------------------------

## Padrões de Raciocínio

- **Mapeamento children vs array fixo →** escolha conforme Σ (alfabeto).
- **Armazenar contadores/weights em nós →** útil para contagem de
  prefíxos e ranking de sugestões.
- **Compressão (radix) →** reduzir memória em troca de lógica mais
  complexa na manipulação de arestas.
- **Usar trie quando há muitas consultas por prefixo →** operações
  de busca por prefixo são O(L), eficientes e ordenáveis.
- **Alternativa:** hash set/map para membership simples — não suporta
  consultas por prefixo eficientes.

Tries são excelentes para autocomplete, dicionários, roteamento de
prefixos e casos onde a ordenação lexicográfica por prefixo importa.
