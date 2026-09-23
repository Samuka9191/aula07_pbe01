# Sistema de Controle de Inventário de Patrimônio

Este é um backend RESTful desenvolvido para gerenciar o inventário patrimonial de uma empresa. Ele permite realizar todas as operações de um CRUD (Criar, Ler, Atualizar e Deletar) de forma simples e rápida, utilizando um arquivo local para simular um banco de dados.

O projeto foi desenvolvido e testado utilizando a IDE **Visual Studio Code (VS Code)**.

---

##  Estrutura de Arquivos do Projeto

Ao abrir a pasta do projeto no VS Code, a estrutura configurada é a seguinte:

*   **`server.js`**: Arquivo principal do projeto. Contém a inicialização do servidor Express, a configuração das rotas HTTP e toda a lógica de manipulação dos dados.
*   **`dados.json`**: Arquivo utilizado como nossa base de dados temporária. Ele guarda os registros do inventário estruturados em formato JSON.
*   **`node_modules/`**: Pasta gerada automaticamente pelo Node.js que armazena o framework Express e todas as suas dependências internas.
*   **`package.json`**: Arquivo de configuração do projeto que lista as dependências utilizadas e os scripts de inicialização.

---

##  Como o Projeto foi Configurado (Passo a Passo)

Para criar este projeto do zero através do prompt de comando (**CMD**), foram executados os seguintes comandos na raiz da pasta:

1. **Inicialização do projeto Node.js:**
   ```bash
   npm init -y
   ```
   *(Este comando cria o arquivo package.json com as configurações padrão).*

2. **Instalação do Framework Express:**
   ```bash
   npm install express
   ```
   *(Baixa e instala o Express, gerando a pasta node_modules).*

3. **Configuração do Script de Inicialização:**
   Dentro do arquivo `package.json`, foi adicionado o script `"dev"` para facilitar a execução com o recurso de atualização automática (`--watch`) nativo do Node.js:
   ```json
   "scripts": {
     "dev": "node --watch server.js"
   }
   ```

---

##  Como Executar o Servidor

Para rodar a aplicação em sua máquina local através do **CMD** ou pelo terminal integrado do **VS Code**, execute o seguinte comando:

```bash
npm run dev
```

O terminal exibirá a mensagem indicando que o servidor está ativo. Ele estará pronto para receber requisições em: `http://localhost:3000`

---

## 🛣️ Rotas da API Disponíveis

### 1. Criar um item (`POST /inventario`)
Envia um novo item para ser adicionado ao inventário. O `id` é gerado automaticamente.
*   **Exemplo de Corpo (JSON):**
    ```json
    {
      "item": "Notebook Dell",
      "local": "Laboratório 01",
      "dataRegistro": "2026-09-10",
      "valor": 3500.00,
      "patrimonio": "PAT-00125"
    }
    ```

### 2. Listar todos os itens (`GET /inventario`)
Retorna um array com todos os itens salvos dentro do arquivo `dados.json`.

### 3. Consultar um item específico (`GET /inventario/:id`)
Busca as informações detalhadas de um item pelo seu número de ID. Retorna erro `404` caso o ID não exista.

### 4. Atualizar um item (`PUT /inventario/:id`)
Altera os dados de um item existente mantendo o mesmo ID original. É necessário enviar todas as propriedades atualizadas no corpo da requisição.

### 5. Excluir um item (`DELETE /inventario/:id`)
Remove permanentemente o item correspondente ao ID informado do arquivo `dados.json`. Retorna o status de sucesso `204 (No Content)`.

---

## 🔬 Testes e Validações Realizadas
*   **Persistência local:** Todas as inclusões, alterações e exclusões modificam diretamente o arquivo `dados.json` em tempo real.
*   **Tratamento de erros:** Caso tente buscar, atualizar ou deletar um ID que não exista, a API responde corretamente informando que o registro não foi encontrado.
