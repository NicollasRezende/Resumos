Módulo 4 - Gerenciamento de Memória

Parte 1: Visão Geral da Gerenciamento de Memória

Conceitos Básicos:

*   A memória principal é uma área de armazenamento temporária e de acesso rápido para programas e dados em uso ativo.
*   Como a memória é um recurso limitado, o sistema operacional deve gerenciá-la de forma eficiente.
*   Gerenciamento de memória refere-se às técnicas e algoritmos utilizados pelo SO para alocar e desalocar porções da memória conforme necessário.

Requisitos do Gerenciamento de Memória:

1.  Relocação: Habilidade de alocar processos em diferentes áreas da memória.
2.  Proteção: Prevenção de interferência entre processos.
3.  Compartilhamento: Permitir que áreas de memória sejam compartilhadas.
4.  Lógica vs Física: Separar visões lógica e física da memória.
5.  Segmentação: Dividir espaço lógico em segmentos.

Parte 2: Alocação Estática vs Dinâmica de Memória

Alocação Estática:

*   Memória dividida em partições de tamanho fixo durante inicialização.
*   Processo inteiro deve caber em uma única partição.
*   Simples, mas leva à fragmentação interna e externa da memória.

Alocação Dinâmica:

*   Processos são alocados dinamicamente em blocos livres vagos na memória.
*   Melhor aproveitamento, mas risco de fragmentação externa.
*   Requer técnicas como compactação, memória virtual e paginação.

Parte 3: Particionamento de Memória

Particionamento Estático:

*   Memória dividida em partições fixas de tamanhos iguais ou desiguais.
*   Partições maiores atribuídas a grandes processos.
*   Baixa flexibilidade e fragmentação interna/externa.

Particionamento Dinâmico:

*   Não há divisões fixas, processos são alocados em blocos livres.
*   Técnicas: First-Fit, Best-Fit, Worst-Fit.
*   Problema da fragmentação externa.

Compactação e Memória Virtual:

*   Compactação move processos para combinar buracos livres.
*   Memória virtual mapeia memória lógica para física através de paginação.

Parte 4: Paginação de Memória

Conceitos de Paginação:

*   Memória física e lógica divididas em blocos de tamanho fixo (páginas).
*   Páginas lógicas mapeadas para páginas físicas através de tabelas.
*   Permite executar processos maiores que a memória física disponível.

Estruturas de Dados:

*   Tabela de Páginas: Mapeia páginas lógicas para páginas físicas.
*   Estrutura de Quadros: Mantém quadros físicos disponíveis.
*   Bit de Presença: Indica se página está na memória ou em disco.

Troca de Páginas (Paging):

*   Processo de transferir páginas entre memória e disco quando necessário.
*   Causado por page faults quando página necessária não está na memória.
*   Uso de áreas de swap no disco para armazenar páginas não usadas.

Algoritmos de Substituição de Páginas:

*   Ideal: Substitui página que não será mais referenciada.
*   FIFO, Ótimo, LRU, Envelhecimento, Relógio.

Parte 5: Segmentação de Memória

Conceitos de Segmentação:

*   Memória lógica dividida em segmentos de tamanhos variados.
*   Cada segmento tem um mapeamento separado para memória física.
*   Permite compartilhamento de memória entre processos.

Tabela de Segmentos:

*   Mantém informações base, limite para cada segmento.
*   Controla acesso e proteção por segmento.

Benefícios da Segmentação:

*   Flexibilidade em alocar segmentos de diferentes tamanhos.
*   Compartilhamento facilitado de bibliotecas e dados.
*   Proteção de memória por segmento.

Integração com Paginação:

*   Segmentação com Paginação: Combina vantagens de ambos.
*   Segmentos paginados individualmente para gerenciamento eficiente.

Parte 6: Memória Virtual e Gerenciamento de Espaço de Endereçamento

Conceitos de Memória Virtual:

*   Abstração que separa memória lógica da física.
*   Permite executar processos maiores que a memória física.
*   Uso de espaço de swap no disco para memória não presente.

Benefícios:

*   Simplifica programação pelo uso de grandes espaços lógicos.
*   Permite multiprogramação eficiente.
*   Proteção e isolamento de processos.

Técnicas de Gerenciamento de Espaço:

*   Paginação sob demanda: Apenas páginas necessárias são carregadas.
*   Memória compartilhada: Vários processos compartilham páginas de código/dados.
*   Mapeamento de arquivos: Arquivos mapeados diretamente na memória.

Considerações de Desempenho:

*   Políticas de pré-paginação e cache de memória.
*   Algoritmos eficientes para substituição de páginas.
*   Melhorias como memória unificada e compressão.