Base de Conhecimento de Linguagens de Programação

Este é um projeto de front-end que cria uma interface web interativa para explorar uma lista de linguagens de programação. A aplicação permite que o usuário visualize e filtre as linguagens com base em um termo de busca, apresentando as informações de forma clara e com um design moderno e atraente.

Funcionalidades Principais

1. Visualização de Dados: Ao carregar, a página está pronta para exibir uma coleção de "cards", cada um representando uma linguagem de programação.
2. Busca Dinâmica: O usuário pode digitar um termo no campo de busca (como "Java", "1995" ou "segurança") e clicar no botão "Buscar". A aplicação então filtra a lista de linguagens, exibindo apenas aquelas cujo nome ou descrição correspondem ao termo pesquisado.
3. Layout Responsivo: A interface se adapta a diferentes tamanhos de tela (desktop, tablet e mobile), garantindo uma boa experiência de uso em qualquer dispositivo.
4. Links Externos: Cada card contém um link "Saiba mais" que direciona o usuário para a documentação oficial ou uma página de referência da respectiva linguagem, abrindo em uma nova aba.

Tecnologias Utilizadas

O projeto é construído com a base da web moderna:

HTML (index.html): É usado para estruturar a página, definindo os elementos principais como o cabeçalho (header), a área de conteúdo (main), o campo de busca (input), o botão (button) e o rodapé (footer).

CSS (style.css): Responsável por toda a estilização visual. O CSS define:
Um tema "tech" escuro com cores neon (ciano sobre fundo preto).
Fontes customizadas (Share Tech Mono) para reforçar a estética.
Uso de variáveis CSS (:root) para um gerenciamento de cores mais fácil e consistente.
Efeitos de hover e focus que adicionam interatividade e feedback visual, como brilhos e transições suaves.
Layout responsivo através de Media Queries (@media), que ajustam a disposição dos elementos em telas menores.

JavaScript (script.js): É o cérebro da aplicação, controlando toda a lógica e interatividade.
Manipulação do DOM: Seleciona elementos do HTML para poder interagir com eles (ler o valor do campo de busca, adicionar os cards na página, etc.).
Assincronismo (async/await): Utiliza a função fetch para carregar os dados das linguagens de programação de forma assíncrona a partir de um arquivo local.
Dados Externos (data.json): As informações sobre as linguagens (nome, ano, descrição e link) são armazenadas em um arquivo JSON, separando os dados da lógica da aplicação. Isso facilita a atualização e manutenção das informações sem precisar alterar o código JavaScript.

Como o Processo Funciona

O fluxo de execução da aplicação é o seguinte:

1. Carregamento da Página: O navegador carrega o index.html, que por sua vez carrega o style.css para aplicar os estilos e o script.js para adicionar a interatividade.

2. Ação do Usuário: O usuário digita um termo no campo de busca e clica no botão "Buscar".

3. Execução do JavaScript: O clique no botão aciona a função iniciarBusca().
   
4. Carregamento dos Dados (se necessário): Dentro de iniciarBusca(), o script verifica se os dados do arquivo data.json já foram carregados.
Na primeira busca: A variável dados está vazia. O script usa fetch("data.json") para fazer uma requisição e buscar o conteúdo do arquivo. O await garante que o código espere a resposta. Após receber, ele converte o texto JSON em um array de objetos JavaScript.
Em buscas subsequentes: Os dados já estão armazenados na variável dados, então o script pula a etapa de carregamento, otimizando o desempenho.

5. Filtragem: O script pega o valor digitado pelo usuário, converte para letras minúsculas (para uma busca não sensível a maiúsculas/minúsculas) e utiliza o método filter() no array de dados. Esse método cria um novo array contendo apenas as linguagens cujo nome ou descricao incluem o termo buscado.

6. Renderização dos Cards: A função renderizarCards() é chamada com os dados filtrados.
Primeiro, ela limpa qualquer conteúdo existente dentro do contêiner de cards (.card-container).
Em seguida, ela percorre (for...of) o array de dados filtrados e, para cada linguagem, cria dinamicamente um elemento <article> com as informações formatadas em HTML.
Finalmente, cada novo card é adicionado à página usando appendChild().

Este ciclo se repete toda vez que o usuário realiza uma nova busca, garantindo que a interface seja sempre atualizada com os resultados correspondentes.
