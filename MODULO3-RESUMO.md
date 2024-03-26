Módulo 3 - Arquivos e Sistemas de Arquivos

Parte 1: Arquivos e Sistemas de Arquivos

Definição e Conceitos de Arquivos:

*   Um arquivo é uma coleção de dados ou informações relacionadas, armazenadas em dispositivos de armazenamento não voláteis como discos rígidos, SSDs, etc.
*   Atua como mecanismo de abstração, permitindo que dados sejam armazenados de forma persistente e recuperados posteriormente.
*   Cada arquivo possui um nome único atribuído durante sua criação, usado para identificá-lo e referenciá-lo.
*   As regras e convenções para nomear arquivos variam entre diferentes sistemas operacionais, mas geralmente incluem restrições de caracteres, extensões de arquivo, etc.
*   Os sistemas operacionais fornecem uma variedade de operações em arquivos como criar, ler, gravar, excluir, renomear, entre outras através de chamadas de sistema ou APIs.

Estruturas de Arquivos:

1.  Sequência de Bytes: O arquivo é tratado como um fluxo bruto de bytes, sem qualquer estrutura imposta pelo sistema operacional. Todo o gerenciamento de estrutura e interpretação de conteúdo fica a cargo dos programas de aplicativos.
2.  Registros de Tamanho Fixo: O arquivo é dividido em uma sequência de registros, cada um com um tamanho fixo predefinido. Facilita o acesso direto a registros específicos. Usado em aplicações onde os dados têm um layout rígido.
3.  Árvore de Registros: Os dados são organizados em uma estrutura hierárquica de nós em árvore. Cada nó contém uma chave e ponteiros para os registros reais armazenados em blocos. Adequado quando a estrutura de dados necessita ser facilmente pesquisável.

Tipos de Arquivos:

1.  Regulares: Contêm dados binários ou texto comum do usuário, como documentos, planilhas, imagens, executáveis, etc.
2.  Diretórios: Arquivos especiais que armazenam a estrutura hierárquica do sistema de arquivos, mapeando nomes de arquivos/diretórios para seus metadados e localizações.
3.  Especiais de Caracteres: Modelam dispositivos de entrada/saída orientados a caracteres, como terminais, impressoras e dispositivos seriais.
4.  Especiais de Blocos: Modelam dispositivos de armazenamento em bloco, como discos rígidos, pen drives, etc. Usados pelo sistema operacional para acessar seu conteúdo bruto.

Métodos de Acesso a Arquivos:

1.  Acesso Sequencial: Os dados são lidos ou gravados sequencialmente, a partir do início do arquivo, na ordem em que foram originalmente gravados. Apropriado para fluxos de dados contínuos.
2.  Acesso Direto: Permite acesso direto a registros específicos dentro do arquivo, através de seu número ou offset. Requer que os registros sejam de tamanho fixo para facilitar o cálculo do deslocamento. Útil para aplicações que precisam acessar dados de forma não sequencial.

Atributos de Arquivos:

*   Os sistemas de arquivos mantêm metadados ou atributos associados a cada arquivo, que fornecem informações sobre suas propriedades e estado.
*   Atributos comuns incluem: tamanho do arquivo, permissões/proteção, proprietário, timestamps (criação, última modificação, último acesso), flags especiais, etc.
*   Alguns atributos são definidos quando o arquivo é criado, enquanto outros podem ser modificados pelo usuário ou atualizados pelo sistema operacional conforme o arquivo é acessado ou modificado.
*   Os atributos são usados pelo sistema operacional para gerenciar, proteger e rastrear o uso dos arquivos.

Parte 2: Sistemas de Diretórios

Diretórios Simples:

*   A abordagem mais simples para organizar arquivos é ter um único diretório contendo entradas para todos os arquivos no sistema.
*   Vantagem: simplicidade e facilidade de encontrar arquivos.
*   Desvantagem: limitado a um único usuário, dificuldade em lidar com grandes quantidades de arquivos, potencial para conflitos de nomes.

Diretórios de Dois Níveis:

*   Cada usuário possui seu próprio diretório privado, permitindo que usuários diferentes tenham arquivos com o mesmo nome.
*   Evita conflitos de nomenclatura entre usuários, mas ainda limita a capacidade de organização de arquivos de um único usuário.

Diretórios Hierárquicos:

*   Os arquivos são organizados em uma estrutura hierárquica em forma de árvore, com subdiretórios aninhados sob diretórios principais.
*   Permite organização flexível e lógica dos arquivos com base em critérios como projeto, tipo de dados, proprietário, etc.
*   O diretório raiz é o ancestral comum de todos os outros diretórios e arquivos no sistema de arquivos.

Nomeação de Caminhos:

1.  Caminho Absoluto: Especifica o caminho completo do diretório raiz até o arquivo em questão, começando com o caractere separador de diretório (/ em Unix, \\ em Windows).
2.  Caminho Relativo: Especifica o caminho do arquivo em relação ao diretório atual de trabalho, sem começar pelo diretório raiz.

Implementações de Sistemas de Diretórios:

*   Linux: Usa uma estrutura de diretório hierárquica baseada em "/", o diretório raiz. Convenções de nomenclatura específicas para diretórios como /home, /etc, /usr.
*   Windows: Estrutura hierárquica baseada em unidades de disco (C:, D:, etc.). Arquivos e diretórios existem dentro dessas unidades.

Parte 3: Implementação e Segurança de Sistemas de Arquivos

Implementação de Estruturas de Arquivos:

1.  Alocação Contígua: O arquivo é armazenado como um bloco contíguo de blocos de disco consecutivos. Simples, porém sujeito à fragmentação com arquivos de tamanhos variados.
2.  Lista Encadeada: Os blocos de disco usados pelo arquivo são encadeados usando ponteiros. Permite que os blocos estejam espalhados, mas acesso é sequencial.
3.  Lista Encadeada com Tabela (FAT): Uma tabela em memória principal mantém os endereços dos blocos na lista encadeada para acesso mais rápido.
4.  I-nodes: Cada arquivo tem uma estrutura i-node associada que armazena seus atributos e endereços de blocos de disco. Acessos indiretos através de camadas adicionais de endereçamento.

Gerenciamento do Espaço em Disco:

*   O sistema de arquivos deve cuidadosamente gerenciar e alocar o espaço em disco conforme arquivos são criados, modificados e excluídos.
*   Lista Encadeada de Blocos Livres: Cada bloco livre mantém um ponteiro para o próximo bloco livre, formando uma lista encadeada.
*   Mapa de Bits: Um vetor de bits grandes o suficiente para ter um bit representando cada bloco de armazenamento no disco. 1 indica bloco alocado, 0 indica livre.

Segurança e Proteção de Arquivos:

*   Os sistemas de arquivos fornecem mecanismos para proteger arquivos contra acessos não autorizados e operações prejudiciais.
*   Senhas e Autenticação: Senha ou autenticação requerida antes de permitir qualquer acesso ao arquivo.
*   Grupos de Usuários: Os usuários são categorizados em grupos, com permissões de acesso atribuídas em nível de grupo.
*   Listas de Controle de Acesso (ACLs): Fornecem controle detalhado das permissões de cada usuário/grupo sobre operações específicas (leitura, gravação, execução).
*   Outros Mecanismos: Criptografia de dados, logs de auditoria, cotas de uso de disco, listas de revogação de acesso, etc.