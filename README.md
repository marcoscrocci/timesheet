# Comandos

## Pr�-requisitos
Voc� precisa do Node.js v16.13.0 ou superior para este guia (saiba mais sobre os requisitos do sistema).

1. Crie um projeto TypeScript e configure o Prisma <br>
Como primeiro passo, crie um diret�rio de projeto e navegue at� ele:

> mkdir timesheet <br>
cd timesheet

A seguir, inicialize um projeto TypeScript usando npm:

> npm init -y <br>
npm install typescript ts-node @types/node --save-dev

Isso cria um package.json com uma configura��o inicial para seu aplicativo TypeScript.

Consulte as instru��es de instala��o para saber como instalar o Prisma usando um gerenciador de pacotes diferente.

Agora, inicialize o TypeScript:

> npx tsc --init

Em seguida, instale a CLI do Prisma como uma depend�ncia de desenvolvimento no projeto:

> npm install prisma --save-dev

Por fim, configure o Prisma com o comando init da CLI do Prisma:

> npx prisma init --datasource-provider sqlite

Isso cria um novo diret�rio prisma com seu arquivo de esquema Prisma e configura o SQLite como seu banco de dados. Agora voc� est� pronto para modelar seus dados e criar seu banco de dados com algumas tabelas.

2. Modele seus dados no esquema Prisma <br>
O esquema Prisma fornece uma maneira intuitiva de modelar dados. Adicione os seguintes modelos ao seu schema.prismaarquivo:

prisma/schema.prisma

Os modelos no esquema Prisma t�m dois prop�sitos principais:

- Representar as tabelas no banco de dados subjacente
- Servir como base para a API Prisma Client gerada

Na pr�xima se��o, voc� mapear� esses modelos para tabelas de banco de dados usando Prisma Migrate.

3. Execute uma migra��o para criar suas tabelas de banco de dados com Prisma Migrate <br>
Neste ponto, voc� tem um esquema Prisma, mas ainda n�o tem banco de dados. Execute o seguinte comando em seu terminal para criar o banco de dados SQLite e as Usertabelas Postrepresentadas por seus modelos:

> npx prisma migrate dev --name init 

Este comando fez duas coisas:

- Ele cria um novo arquivo de migra��o SQL para esta migra��o no prisma/migrationsdiret�rio.
- Ele executa o arquivo de migra��o SQL no banco de dados.

Como o arquivo de banco de dados SQLite n�o existia antes, o comando tamb�m o criou dentro do prismadiret�rio com o nome dev.dbdefinido pela vari�vel de ambiente no .envarquivo.

Parab�ns, agora voc� tem seu banco de dados e tabelas prontos. Vamos aprender como voc� pode enviar algumas consultas para leitura e grava��o de dados!


#### Salvar uma nova migra��o:

> npx prisma migrate save --name add_index_to_nome

#### Aplicar a migra��o:
> npx prisma migrate up

<br>

### Projeto de exemplo:
https://github.com/rocketseat-content/prisma_decode/tree/master/src
