# Calendário de Compras

**Visão Geral**

Este projeto tem como objetivo substituir uma planilha antiga de "agenda de compras" por uma interface web mais visual e intuitiva.  
Com ele, as unidades conseguem filtrar as informações pela sua filial e visualizar, de forma consolidada, as solicitações de compras diárias.

**Tecnologias Utilizadas**

- **HTML5**: Estrutura da página.
- **CSS3**: Estilização e responsividade.
- **JavaScript (ES6)**: Lógica de interação e manipulação do DOM.
- **Python**: Conversão da planilha do Excel em um arquivo JSON consumido pelo JavaScript.

**Estrutura do Código**

O código está dividido nas seguintes partes:

1. **HTML**
   - Define a estrutura da página, incluindo o cabeçalho, a área de filtro, a navegação dos meses, o calendário e o modal para exibição dos detalhes.

2. **CSS**
   - Responsável pela estilização dos elementos, como:
     - **Estilo Geral**: Define cores, fontes e espaçamentos.
     - **Filtro e Navegação**: Estiliza o seletor de unidades e os botões de navegação entre os meses.
     - **Calendário**: Organiza os dias em um _grid_ e destaca os dias que possuem compras.
     - **Modal**: Estiliza a janela de detalhes exibida quando um dia é selecionado.

3. **JavaScript**
   - **Variáveis Globais**:
     - `dados`: Armazena as informações carregadas do arquivo JSON.
     - `mesAtual` e `anoAtual`: Determinam o mês e o ano a serem exibidos.
   - **Funções Principais**:
     - **`formatarData(data)`**: Formata datas do formato `D/M/AAAA` para `DD/MM/AAAA`.
     - **`atualizarTituloMes()`**: Atualiza o título com o mês e ano atuais.
     - **`gerarOpcoesFilial()`**: Gera dinamicamente as opções do filtro com base nas filiais disponíveis.
     - **`gerarCalendario(unidadeSelecionada = '')`**: Constrói o calendário, destacando os dias com compras.
     - **`exibirDetalhes(dia)`**: Exibe um modal com os detalhes das compras ao clicar em um dia.
     - **`fecharModal()`**: Fecha o modal de detalhes.
     - **`filtrarPorUnidade()`**: Regenera o calendário de acordo com a unidade selecionada.
     - **`mudarMes(direcao)`**: Permite a navegação entre meses.

**Fluxo de Funcionamento**

1. **Carregamento Inicial**:  
   Ao carregar a página, o JavaScript realiza um _fetch_ para carregar os dados do arquivo `agenda.json`.  
   Em seguida, são geradas as opções do filtro, o título do mês/ano e o calendário com os dias do mês atual, destacando os dias que possuem compras.

2. **Interação do Usuário**:  
   - **Filtragem**: O usuário pode selecionar uma filial para visualizar somente as compras correspondentes.
   - **Navegação de Meses**: Utilizando os botões "Mês Anterior" e "Próximo Mês", o calendário é atualizado conforme o mês selecionado.
   - **Exibição de Detalhes**: Ao clicar em um dia, um modal exibe as informações detalhadas das compras daquele dia.

3. **Fechamento do Modal**:  
   Basta clicar no ícone de fechar (×) para voltar à visualização do calendário.

**Considerações Finais**

- **Manutenção**:  
  A organização e a documentação das funções facilitam a manutenção e futuras atualizações do sistema.

- **Extensibilidade**:  
  O sistema pode ser facilmente expandido para incluir novas funcionalidades ou filtros.

- **Experiência do Usuário**:  
  A interface intuitiva e o uso de modais melhoram a experiência em comparação com a antiga planilha.


