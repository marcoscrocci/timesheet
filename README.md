# Comandos

## Pré-requisitos
Você precisa do Node.js v16.13.0 ou superior para este guia (saiba mais sobre os requisitos do sistema).

1. Crie um projeto TypeScript e configure o Prisma <br>
Como primeiro passo, crie um diretório de projeto e navegue até ele:

> mkdir timesheet <br>
cd timesheet

A seguir, inicialize um projeto TypeScript usando npm:

> npm init -y <br>
npm install typescript ts-node @types/node --save-dev

Isso cria um package.json com uma configuração inicial para seu aplicativo TypeScript.

Consulte as instruções de instalação para saber como instalar o Prisma usando um gerenciador de pacotes diferente.

Agora, inicialize o TypeScript:

> npx tsc --init

Em seguida, instale a CLI do Prisma como uma dependência de desenvolvimento no projeto:

> npm install prisma --save-dev

Por fim, configure o Prisma com o comando init da CLI do Prisma:

> npx prisma init --datasource-provider sqlite

Isso cria um novo diretório prisma com seu arquivo de esquema Prisma e configura o SQLite como seu banco de dados. Agora você está pronto para modelar seus dados e criar seu banco de dados com algumas tabelas.

2. Modele seus dados no esquema Prisma <br>
O esquema Prisma fornece uma maneira intuitiva de modelar dados. Adicione os seguintes modelos ao seu schema.prismaarquivo:

prisma/schema.prisma

Os modelos no esquema Prisma têm dois propósitos principais:

- Representar as tabelas no banco de dados subjacente
- Servir como base para a API Prisma Client gerada

Na próxima seção, você mapeará esses modelos para tabelas de banco de dados usando Prisma Migrate.

3. Execute uma migração para criar suas tabelas de banco de dados com Prisma Migrate <br>
Neste ponto, você tem um esquema Prisma, mas ainda não tem banco de dados. Execute o seguinte comando em seu terminal para criar o banco de dados SQLite e as Usertabelas Postrepresentadas por seus modelos:

> npx prisma migrate dev --name init 

Este comando fez duas coisas:

- Ele cria um novo arquivo de migração SQL para esta migração no prisma/migrationsdiretório.
- Ele executa o arquivo de migração SQL no banco de dados.

Como o arquivo de banco de dados SQLite não existia antes, o comando também o criou dentro do prismadiretório com o nome dev.dbdefinido pela variável de ambiente no .envarquivo.

Parabéns, agora você tem seu banco de dados e tabelas prontos. Vamos aprender como você pode enviar algumas consultas para leitura e gravação de dados!


#### Salvar uma nova migração:

> npx prisma migrate save --name add_index_to_nome

#### Aplicar a migração:
> npx prisma migrate up

<br>

### Projeto de exemplo:
https://github.com/rocketseat-content/prisma_decode/tree/master/src
