Documentação do Projeto: Calendário de Compras
Visão Geral
Este projeto tem como objetivo substituir uma planilha de "agenda de compras" por uma interface web mais visual e intuitiva. Com ele, os usuários (unidades) podem filtrar os dados por sua respectiva unidade e visualizar, de forma consolidada, as solicitações de compras diárias. O front-end é desenvolvido com HTML, CSS e JavaScript, enquanto os dados são carregados a partir de um arquivo JSON (gerado via um script Python que converte uma planilha do Excel para JSON).

Estrutura do Código
1. HTML
Cabeçalho (<head>):

Define a codificação (UTF-8) e a responsividade.
Importa a fonte Roboto do Google Fonts.
Contém a seção <style> com a definição de estilos (CSS) para o layout e os componentes do calendário.
Corpo (<body>):

Header: Exibe a logo da empresa.
Título: "Calendário de Compras".
Filtro por Unidade: Um <select> que permite filtrar os dados com base na unidade (filial).
Navegação de Meses: Botões para avançar ou retroceder o mês e um elemento <span> para exibir o mês/ano atual.
Calendário: Um <div> com a classe calendar que será preenchido dinamicamente via JavaScript com os dias do mês.
Modal: Um modal para exibir os detalhes de cada dia quando clicado.
2. CSS
Estilos Gerais: Define o layout, cores, espaçamentos e tipografia utilizando a fonte Roboto.
Estilização do Filtro e Navegação de Meses: Define estilos para os elementos de filtro e botões de navegação.
Estilização do Calendário:
Utiliza grid layout para distribuir os dias da semana e os dias do mês.
Destaca células com compras (classe .has-agenda) e o dia selecionado (classe .selected).
Modal: Estilos para exibir o modal centralizado na tela e o botão de fechar.
3. JavaScript
Variáveis Globais:
dados: Array que armazenará os dados carregados do arquivo JSON.
dataAtual, mesAtual e anoAtual: Variáveis para gerenciar a data atual e atualizar a visualização do calendário.
Funções Principais:
formatarData(data)
Formata uma data do formato D/M/AAAA para DD/MM/AAAA.
Exemplo de uso:

js
Copiar
formatarData("5/9/2025"); // retorna "05/09/2025"
atualizarTituloMes()
Atualiza o elemento que exibe o mês e o ano atuais.
Utiliza um array de meses em português para formatar a string.

gerarOpcoesFilial()
Gera dinamicamente as opções do filtro de unidades (filiais) com base nos dados do JSON.

Cria a opção padrão "Todas as Unidades".
Extrai e ordena as filiais únicas presentes no JSON e as adiciona ao <select>.
gerarCalendario(unidadeSelecionada = '')
Constrói o calendário para o mês e ano atuais.

Cria os cabeçalhos dos dias da semana.
Calcula o offset (células vazias) para alinhar o primeiro dia do mês de acordo com o dia da semana.
Cria as células correspondentes aos dias do mês.
Filtra os dados do JSON para identificar os dias que possuem compras e aplica a classe .has-agenda para destacar esses dias.
exibirDetalhes(dia)
Exibe os detalhes das compras para um dia específico em um modal.

Remove a classe .selected dos dias previamente selecionados.
Adiciona a classe .selected ao dia clicado.
Filtra os dados do JSON para obter as compras do dia (considerando também o filtro por unidade, se aplicável).
Monta o conteúdo HTML com os detalhes de cada compra (data de abertura, categoria, filial, previsão de entrega) e exibe no modal.
fecharModal()
Fecha o modal de detalhes, ocultando-o da visualização.

filtrarPorUnidade()
Chamada quando o usuário seleciona uma filial no <select>.

Obtém o valor selecionado e regenera o calendário para exibir apenas as compras daquela unidade.
Remove a seleção de qualquer dia previamente selecionado.
mudarMes(direcao)
Permite a navegação entre os meses.

Atualiza as variáveis mesAtual e anoAtual de acordo com a direção (-1 para mês anterior, 1 para próximo mês).
Atualiza o título com o mês/ano e regenera o calendário mantendo o filtro de filial, se estiver ativo.
window.onload
Quando a página carrega:

Tenta carregar os dados do arquivo agenda.json via fetch.
Em caso de sucesso, armazena os dados, gera as opções do filtro e renderiza o calendário.
Em caso de erro, exibe uma mensagem no console e alerta o usuário.
Fluxo de Funcionamento
Carregamento Inicial:
Ao carregar a página, o script realiza um fetch para carregar o arquivo agenda.json. Se os dados forem carregados corretamente, o sistema:

Popula o filtro de unidades.
Atualiza o título com o mês e ano atuais.
Gera o calendário com os dias do mês atual, destacando aqueles que possuem compras.
Interação do Usuário:

Filtragem: O usuário pode selecionar uma unidade no filtro, o que faz com que o calendário seja regenerado para exibir apenas as compras da filial selecionada.
Navegação de Meses: O usuário pode navegar entre os meses utilizando os botões "Mês Anterior" e "Próximo Mês". O título e o calendário são atualizados de acordo.
Visualização de Detalhes: Ao clicar em um dia, o sistema exibe um modal com os detalhes das compras daquele dia. O dia selecionado é destacado no calendário.
Fechamento do Modal:
O usuário pode fechar o modal clicando no "X" ou fora da área de conteúdo, retornando à visualização do calendário.

Tecnologias Utilizadas
Front-end:

HTML5: Estrutura e semântica da página.
CSS3: Estilização e responsividade da interface.
JavaScript (ES6): Lógica para manipulação do DOM, interação com o usuário e consumo de dados do JSON.
Back-end / Suporte:

Arquivo JSON: Dados gerados via script Python que converte a planilha Excel para JSON. Este JSON contém informações como data de abertura, categoria, filial e previsão de entrega das compras.
Considerações Finais
Manutenção:
A documentação interna e a organização das funções facilitam a manutenção e futuras atualizações do sistema.

Extensibilidade:
O sistema pode ser expandido para incluir mais filtros ou funcionalidades, bastando adicionar novas funções e atualizar a interface conforme necessário.

Experiência do Usuário:
O uso de um modal para detalhes e a navegação intuitiva entre os meses melhoram significativamente a experiência dos usuários em comparação com a planilha antiga.
