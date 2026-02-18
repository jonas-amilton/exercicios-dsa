# Resumo --- Notação Big O

A notação Big O descreve o limite superior do crescimento do custo
computacional de um algoritmo em função do tamanho da entrada (n). Ela
abstrai constantes e fatores menores, focando na taxa de crescimento
assintótica.

------------------------------------------------------------------------

## Tabela de Complexidade

  ------------------------------------------------------------------------
  Notação          Classificação             Exemplos Típicos
  ---------------- ------------------------- -----------------------------
  O(1)             Constante                 Acesso por índice em array,
                                             lookup em tabela hash

  O(log n)         Logarítmica               Busca binária, operações em
                                             árvores balanceadas

  O(n)             Linear                    Iteração simples, varredura
                                             sequencial

  O(n log n)       Linearítmica              Merge Sort, Heap Sort, Quick
                                             Sort (caso médio)

  O(n²)            Quadrática                Loops duplos, Bubble Sort

  O(2ⁿ)            Exponencial               Fibonacci recursivo ingênuo,
                                             geração de subconjuntos

  O(n!)            Fatorial                  Geração de todas as
                                             permutações
  ------------------------------------------------------------------------

------------------------------------------------------------------------

## Comparação Numérica (n = 1.000)

  Complexidade   Estimativa de Operações
  -------------- -------------------------
  O(1)           1
  O(log n)       \~10
  O(n)           1.000
  O(n log n)     \~10.000
  O(n²)          1.000.000

Observação: valores aproximados considerando log₂(1000) ≈ 10.

------------------------------------------------------------------------

## Complexidade de Espaço

A notação Big O também se aplica ao consumo de memória adicional.

Aspectos críticos: - Estruturas auxiliares (arrays, mapas, buffers
temporários) - Recursão (uso da pilha de chamadas) - Cópias implícitas
de dados

------------------------------------------------------------------------

## Exercícios Comentados

### Exercício 1 --- Loop Simples

Código:

for i in range(n): soma += i

**Complexidade:** O(n)

O bloco é executado exatamente n vezes. Não há dependência aninhada.

------------------------------------------------------------------------

### Exercício 2 --- Encontrar Pares com Soma X

#### Abordagem 1 --- Força Bruta

Dois loops aninhados comparando todos os pares possíveis:

-   Tempo: O(n²)
-   Espaço: O(1)

#### Abordagem 2 --- Otimizada com Hash

Estratégia: 1. Percorrer o array uma única vez. 2. Para cada elemento
`x`, verificar se `(X - x)` já foi visto. 3. Registrar `x` em uma tabela
hash.

-   Tempo: O(n)
-   Espaço: O(n)

A verificação em tabela hash ocorre em tempo constante médio.

------------------------------------------------------------------------

## Padrões de Reconhecimento

Heurísticas práticas:

-   Loop simples → O(n)
-   Loops aninhados dependentes → O(n²)
-   Divisão do problema pela metade → O(log n)
-   Divisão + processamento linear → O(n log n)
-   Exploração combinatória → O(2ⁿ) ou O(n!)

A análise correta depende de identificar a operação dominante e ignorar
constantes e termos de menor ordem.