# Arrays --- Operações e Análise de Complexidade

Arrays são estruturas de dados baseadas em memória contígua, o que
permite acesso direto por índice, porém impõe custo quando há
necessidade de deslocamento de elementos.

------------------------------------------------------------------------

## Tabela de Complexidade

  -----------------------------------------------------------------------------
  Operação            Complexidade de Tempo        Observações Técnicas
  ------------------- ---------------------------- ----------------------------
  Acesso por índice   O(1)                         Endereçamento direto na
                                                   memória

  Busca (array não    O(n)                         Percorre sequencialmente até
  ordenado)                                        encontrar

  Inserção no final   O(1)                         Vetores dinâmicos realocam
  (amortizada)                                     ocasionalmente

  Inserção no início  O(n)                         Requer deslocamento de todos
                                                   os elementos

  Remoção no final    O(1)                         Operação equivalente a
                                                   `pop()`

  Remoção em posição  O(n)                         Necessário deslocar
  arbitrária                                       elementos subsequentes

  Redimensionamento   O(n) amortizado              Realocação e cópia para novo
  interno                                          buffer
  -----------------------------------------------------------------------------

------------------------------------------------------------------------

## Complexidade de Espaço

-   Espaço principal ocupado pelo array: **O(n)**
-   Estruturas auxiliares (quando utilizadas): crescimento proporcional
    à necessidade da solução

------------------------------------------------------------------------

## Exercícios Comentados

### Exercício 1 --- Acesso Direto

Qual a complexidade da operação `arr[0]`?

**Resposta:** O(1)\
O índice é traduzido diretamente para um endereço de memória, sem
necessidade de iteração.

------------------------------------------------------------------------

### Exercício 2 --- Remoção de Duplicatas

#### Abordagem Ingênua

Utilizando dois loops aninhados para comparar todos os pares:

-   Complexidade de tempo: **O(n²)**
-   Complexidade de espaço: **O(1)**

Essa estratégia compara cada elemento com todos os demais.

#### Abordagem Otimizada

Utilizando uma tabela hash para rastrear elementos já vistos:

-   Complexidade de tempo: **O(n)**
-   Complexidade de espaço: **O(n)**

Cada elemento é processado uma única vez, e a verificação de existência
ocorre em tempo constante médio.

------------------------------------------------------------------------

## Padrões de Raciocínio

Alguns padrões recorrentes na análise de arrays:

-   **Acesso direto por índice → O(1)**
-   **Deslocamento de elementos → O(n)**
-   **Uso de estrutura hash para otimização → O(n)**

A escolha da abordagem correta depende das operações mais frequentes no
sistema.\
Se há muitas inserções no início, arrays podem não ser ideais.\
Se predominam leituras por índice, arrays são altamente eficientes.