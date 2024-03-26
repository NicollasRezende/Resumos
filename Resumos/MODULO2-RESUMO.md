Módulo 2 - Processos e Comunicação

Parte 1: Processos

Definição e Conceito:

*   Um processo é um programa em execução, composto por um espaço de endereçamento privado que contém código executável, dados, pilha, contadores de programa e registradores.
*   Enquanto um programa é uma entidade passiva, como um arquivo executável armazenado em disco, um processo é uma entidade ativa com recursos alocados.

Modelo de Processo:

*   Um processo é composto por: programa executável, dados de entrada, dados de saída e um estado atual.
*   O estado inclui valores de registradores da CPU, contadores de programa, conteúdo da memória, além do estado dos recursos do sistema usados.

Criação de Processos:

*   Sistemas operacionais fornecem meios para criar novos processos por:

1.  Inicialização do sistema
2.  Chamada de sistema de criação de processo por outro processo
3.  Requisição explícita de usuário (interface de linha de comando, interface gráfica)
4.  Inicialização de trabalho em lote em sistemas batch

Término de Processos:

*   Saída normal (voluntária): Processo terminou normalmente
*   Saída por erro (voluntária): Processo detectou erro e decidiu terminar
*   Erro fatal (involuntário): Erro que força a terminação (violação de proteção de memória, erro de hardware, etc.)
*   Cancelado por outro processo: Um processo requisita explicitamente que o SO termine outro processo

Hierarquias de Processos:

*   Em sistemas como UNIX, processos podem criar outros processos formando hierarquias como árvores
*   Processo-raiz é criado durante inicialização
*   Processos podem criar filhos que herdam recursos de ambiente do pai
*   Permite modelar aplicações cujas atividades são naturalmente estruturadas como sub-tarefas cooperativas

Estados de um Processo:

1.  Executando (Running): Instruções sendo executadas, processo ativo
2.  Pronto (Ready): Apto a ser executado assim que a CPU estiver disponível
3.  Espera/Bloqueado (Wait/Blocked): Aguardando algum evento como E/S ou sinal para poder prosseguir

*   Transições de estado acontecem por interrupções de sistema, E/S ou agendador

Threads:

*   Uma thread/linha de execução é um fluxo de controle dentro de um processo
*   Um processo pode ter uma ou várias threads
*   Vantagens: Paralelismo, melhor responsividade, economia de recursos, comunicação simples
*   Modelos de implementação: Threads de usuário, Threads de kernel, Híbridas

Implementação e Controle:

*   Bloco de Controle de Processo (PCB) armazena informações de estado
*   Contexto de CPU é armazenado em pilha de sistema durante trocas de contexto
*   Outras estruturas: imagens de memória, listas de recursos, listas encadeadas, etc.

Parte 2: Comunicação Entre Processos

Condições de Disputa/Corrida:

*   Ocorrem quando dois ou mais processos acessam e manipulam dados compartilhados simultaneamente
*   A ordem de execução determina o resultado final, que pode ser inconsistente/incorreto
*   Exemplo: Transferência de conta bancária, escritor/leitor de buffer compartilhado

Regiões Críticas e Exclusão Mútua:

*   Região crítica é uma seção de código que acessa recursos compartilhados
*   Exclusão mútua garante que apenas um processo de cada vez execute em sua região crítica
*   Requisitos: Mutua exclusão, Espera limitada, Não espera desnecessária, Não postergação indefinida

Algoritmos de Exclusão Mútua com Espera Ociosa:

1.  Desabilitar Interrupções: Desabilitar interrupções enquanto em região crítica (incapaz de tratar múltiplos processos)
2.  Variável de Bloqueio: Testar e definir variável de bloqueio antes de entrar na região crítica (sem preempção)
3.  Instrução Especial de Máquina: Usar instruções atômicas especiais como TestAndSet para bloquear

Solução Dormir/Acordar:

*   Uma solução para melhorar a ociosidade pura
*   Chamadas de sistema sleep coloca processo em espera bloqueada
*   Chamadas de sistema wakeup ativam processo bloqueado
*   Consumo de CPU reduzido enquanto bloqueado

Semáforos:

*   Um semáforo é uma variável inteira não-negativa com 2 operações atômicas principais:

1.  down/wait/p: Tenta decrementar o semáforo. Se 0, bloqueia.
2.  up/signal/v: Incrementa o semáforo, desbloqueando algum processo bloqueado no down

*   Tipos: Binários (mutex) controlam acesso a região crítica, Contadores controlam número de recursos disponíveis

Monitores:

*   Um monitor é um módulo ou pacote contendo procedimentos, variáveis e estruturas de dados compartilhadas
*   Somente um processo pode estar ativo dentro do monitor por vez
*   Condições de entrada/saída controlam bloqueio de processos
*   Implementa exclusão mútua inerentemente

Troca de Mensagens:

*   Mecanismo de comunicação processo-processo via troca de mensagens
*   Operações send e receive entre processos
*   Kernel fornece canais/filas lógicas para mensagens
*   Permite sincronização indireta e transferência de dados

Parte 3: Escalonamento de Processos

Escalonador de Processos:

*   Componente do sistema operacional que escolhe qual processo terá acesso à CPU
*   Metas: Máximo throughput, tempo de retorno justo, mínimo tempo de resposta, eficiência de CPU
*   Aplica algoritmos/políticas de escalonamento para escalonamento de processos e threads

Situações de Escalonamento:

1.  Mudança de processo: Novo processo criado e colocado na fila pronta
2.  Processo bloqueado: Processo bloqueado ao aguardar recurso (E/S) liberando a CPU
3.  Processo desbloqueado: Processo desbloqueado pela chegada de recursos
4.  Término de processo: Processo termina liberando recursos
5.  Interrupções periódicas: Temporizador expira forçando decisão de escalonamento

Critérios de Escalonamento:

1.  Utilização da CPU: Manter CPU ocupada 100% do tempo
2.  Throughput: Número de processos completados por unidade de tempo
3.  Tempo de Retorno: Intervalo de submissão até conclusão
4.  Tempo de Espera: Soma dos períodos que processo aguarda na fila pronta
5.  Tempo de Resposta: Tempo até o primeiro retorno da conclusão

Ambientes de Escalonamento:

1.  Sistemas Batch: Preemptivos ou não-preemptivos
2.  Sistemas Interativos: Preemptivos para compartilhar CPU entre processos
3.  Sistemas de Tempo Real: Escalonar processos com restrições de tempo rígidas

Escalonamento de Threads:

1.  Threads de Usuário: Escalonadas pela aplicação/biblioteca de threads
2.  Threads de Kernel: Diretamente escalonadas pelo escalonador de processos do kernel
3.  Threads Híbridas: Mistura dos modelos de usuário e kernel