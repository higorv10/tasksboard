# Gerenciador de Boards 🗂️

Este é um sistema simples para gerenciar boards e cards, onde é possível criar, mover, bloquear, desbloquear e excluir boards e cards, bem como gerenciar suas colunas.

## 🚀 Funcionalidades

- **Criar um novo board** 🆕
- **Selecionar um board existente** 📋
- **Excluir um board** ❌
- **Gerenciar colunas e cards** 📝
  - Criar, mover e bloquear cards
  - Excluir cards
- **Integração com banco de dados** 💾
  - Utiliza Liquibase para gerenciar migrações de banco de dados

## 🛠️ Tecnologias Utilizadas

- **Java 17+** ☕
- **MySQL** 🐬
- **Liquibase** 🔄
- **JDBC** para conexão com o banco de dados

## 📂 Estrutura de Pastas

```bash
src/
├── main/
│   ├── java/
│   │   └── dio/
│   │       └── board/
│   │           ├── ui/                 # Interfaces de usuário
│   │           ├── persistence/        # Persistência (DAO, Entities, etc)
│   │           ├── service/            # Lógica de negócios (Services)
│   │           └── Main.java           # Ponto de entrada da aplicação
│   ├── resources/
│   │   └── db/
│   │       └── changelog/             # Scripts de migração do banco de dados
│   │           └── db.changelog-master.yml
└── pom.xml                             # Dependências do Maven
 
```

## 📦 Dependências
  - Maven para gerenciamento de dependências.

  - JDBC Driver para MySQL: `com.mysql.cj.jdbc.Driver`.

  - Liquibase para migração de banco de dados.

## 🔄 Fluxo de Execução
1. Iniciar a aplicação:

  - O ponto de entrada da aplicação é a classe `Main.java`, que inicializa a migração do banco de dados e, em seguida, exibe o menu principal para o usuário.

2. Operações do Menu:

    O usuário pode escolher entre:

        - Criar um novo board 🆕

        - Selecionar um board existente 📋

        - Excluir um board ❌

        - Sair 🚪

3. Interação com o Banco de Dados:

    - A aplicação usa a classe `BoardService` e outras para realizar operações de CRUD no banco de dados (criação, leitura, atualização e exclusão de boards e cards).

4. Migração do Banco de Dados:

    - Ao iniciar a aplicação, a classe `MigrationStrategy` executa as migrações do banco de dados usando o Liquibase para garantir que o esquema esteja atualizado.

## ⚙️ Como Rodar
1. Clone o repositório:

   ```bash

   git clone https://github.com/higorv10/dio-board.git
   cd dio-board\app
   ```

2. Configure o banco de dados no arquivo `src/main/resources/db/changelog/db.changelog-master.yml`:

    - Altere as credenciais de conexão (usuário, senha, URL do banco) conforme necessário.
  
3. Após clonar o repositório, localize o arquivo `Main.java` no seu diretório local:
   ```css
   [CAMINHO_DO_REPOSITÓRIO]\src\main\java\dio\board\Main.java
   ```

4. Caso esteja utilizando o VSCode, basta abrir o projeto, localizar o arquivo Main.java e clicar com o botão direito sobre ele para selecionar a opção Run. O terminal irá exibir as instruções para interagir com a aplicação.

5. Se preferir rodar a aplicação no Maven via terminal, compile e execute o projeto com os seguintes comandos:

   ```bash

   mvn clean install
   mvn exec:java
   ```

   ```pgsql
   - Siga as instruções no terminal para interagir com o sistema de boards.
   ```

## 🛠️ Migrações do Banco de Dados
O projeto utiliza Liquibase para gerenciar as migrações de banco de dados.

Exemplo de migração (definindo a coluna `unblock_reason` como `NULL`):

```sql
--changeset higor:202503161657
--comment: set unblock_reason nullable
ALTER TABLE BLOCKS MODIFY COLUMN `unblock_reason` VARCHAR(255) `NULL`;
```

## 📋 Exemplo de Uso
1. Criar um novo board:

    - O usuário insere o nome do board e pode adicionar colunas personalizadas além das colunas padrão (`INITIAL`, `PENDING`, `FINAL`, `CANCEL`).

2. Mover cards entre colunas:

    - Os cards podem ser movidos entre as colunas do board, respeitando a ordem de execução.

3. Bloquear ou desbloquear cards:

    - Cards podem ser bloqueados ou desbloqueados com uma razão opcional.

## 📝 Observações
  
  - Certifique-se de que o banco de dados MySQL esteja configurado corretamente antes de rodar a aplicação.
  - As migrações do banco são executadas automaticamente ao iniciar a aplicação, garantindo que a estrutura do banco esteja sempre atualizada.

## 📄 Licença
Este projeto está sob a licença MIT.

