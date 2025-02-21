
![Descricao da sua imagem](https://imgur.com/C8TfWXc.png)

# Titulo do projeto

Aplicação web de lista de compras para o curso de construção de páginas dinâmicas com JavaScript.

## 🔨 Funcionalidades do projeto

A aplicação permite inserir itens em uma lista de forma dinâmica, permitindo a exclusão e edição dos mesmos. Os itens terão o nome e também a data e horário que foram criados. Também é possível selecionar um checkbox para informar que o item foi comprado.

![Inserção no campo de digitação do valor ração de gato, após, é clicado no botão de edição, onde é aberto um popup para digitar o novo do nome item, que foi digitado ração de cachorro. Em seguida, é clicado no botão de exclusão, e o item é excluído.](https://imgur.com/isPj7Xf.gif)

## ✔️ Técnicas e tecnologias utilizadas

As técnicas e tecnologias utilizadas pra isso são:

- `HTML`: criação dos elementos da tela;
- `CSS`: estilização da aplicação;
- `JavaScript`: construção de elementos dinâmicos através da manipulação do DOM.

## 📁 Acesso ao projeto

Você pode [acessar o código fonte do projeto inicial](https://github.com/alura-cursos/3801-javascript-para-web/tree/projeto-base) ou [baixá-lo](https://github.com/alura-cursos/3801-javascript-para-web/archive/refs/heads/projeto-base.zip).

## 🛠️ Abrir e rodar o projeto

Após baixar o projeto, você pode abrir com o Visual Studio Code. Para isso, no menu superior, clique em:

- **File** > **Open Folder** (ou alguma opção similar)
- Procure o local onde o projeto está e o selecione (Caso o projeto seja baixado via zip, é necessário extraí-lo antes de procurá-lo)
- Por fim clique em OK

Ao finalizar esses passos, você pode executar a aplicação com a extensão Live Server 🏆 

### COMANDOS UTILIZADOS:
1- Armazene um botão de salvar em uma variável.
2- Capture o valor do campo de digitação.
3- Evite o comportamento padrão de envio do formulário.
4- Impeça que itens vazios sejam adicionados à lista.
5- Construa dinamicamente cada item da lista com os valores inseridos pelo usuário.

- Comece selecionando os elementos do HTML com os quais vamos interagir: o campo de input (input-item), a lista onde os itens serão exibidos (lista-de-compras) e o botão que será usado para adicionar os itens (adicionar-item). Essas seleções são armazenadas em variáveis para facilitar o uso posterior:
"    const inputItem = document.getElementById("input-item");
     const listaDeCompras = document.getElementById("lista-de-compras");
     const botaoAdicionar = document.getElementById("adicionar-item");
     let contador = 0;"

- Adicione um ouvinte de eventos ao botão "Salvar" com o método addEventListener. Quando o botão é clicado, ele executa a função definida. Dentro dessa função, a primeira ação é evitar o comportamento padrão do formulário com evento.preventDefault(). Isso impede que a página seja recarregada ao enviar o formulário:
"   botaoAdicionar.addEventListener("click", (evento) => {
    evento.preventDefault();"

- Antes de adicionar um item à lista, valide o campo para garantir que o campo de input não está vazio. Se o campo estiver vazio, o código exibe um alerta e interrompe a execução com o comando return:
"   if (inputItem.value === "") {
        alert("Por favor, insira um item!");
        return;
    } "

- Caso o campo esteja preenchido, o código deve criar os elementos necessários para montar o item da lista:
Um <li> para representar o item na lista.
Um <div> com a classe lista-item-container para organizar os conteúdos do item.
Um <input> do tipo checkbox para permitir marcar o item.
Um <p> que contém o texto digitado no input. Esse texto é inserido no elemento <p> com a propriedade innerText:
"   const itemDaLista = document.createElement("li");
    const containerItemDaLista = document.createElement("div");
    containerItemDaLista.classList.add("lista-item-container");
    const inputCheckbox = document.createElement("input");
    inputCheckbox.type = "checkbox";
    inputCheckbox.id = "checkbox-" + contador++;
    const nomeItem = document.createElement("p");
    nomeItem.innerText = inputItem.value;"

- Os elementos criados devem ser organizados. Primeiro, o checkbox e o texto serão adicionados ao div. Depois, o div é anexado ao <li>, e o <li> é adicionado à lista de compras (ul):
   "containerItemDaLista.appendChild(inputCheckbox);
    containerItemDaLista.appendChild(nomeItem);
    itemDaLista.appendChild(containerItemDaLista);
    listaDeCompras.appendChild(itemDaLista);"