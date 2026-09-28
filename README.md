# CheckIn

Bot para Discord desenvolvido em TypeScript para registrar e exibir a entrada de membros no servidor através de cards personalizados.

O CheckIn coleta informações disponíveis pela API oficial do Discord, organiza os dados em uma Tree View e gera um card visual do perfil utilizando o avatar e o banner do usuário.

## Funcionamento

```text
Novo membro entra no servidor
        ↓
Discord Gateway
        ↓
GuildMemberAdd
        ↓
CheckIn
        ↓
Busca informações do usuário
├── identidade
├── criação da conta
├── entrada no servidor
├── cargos
├── boost
├── avatar
├── banner
└── accent color
        ↓
Sharp gera o profile card
        ↓
Embed + imagem
        ↓
#catraca
```

O processo acontece automaticamente enquanto o bot estiver online.

## Recursos

- Detecção automática de novos membros
- Card personalizado de entrada
- Avatar circular sobre o banner
- Banner do perfil quando disponível
- Cor de destaque do usuário
- Número do membro baseado na ordem de entrada
- Data de criação da conta
- Data de entrada no servidor
- Nickname
- Cargos
- Status de boost
- Informações de avatar global e do servidor
- Tree View com informações do membro
- Modo de teste
- Sincronização dos membros existentes
- Reconstrução dos registros da catraca

## Exemplo da Tree View

```text
MEMBER
├─ identity
│  ├─ displayName
│  ├─ username
│  ├─ id
│  └─ bot
│
├─ account
│  ├─ created
│  └─ age
│
├─ guild
│  ├─ joined
│  ├─ member
│  ├─ nickname
│  ├─ pending
│  └─ boostingSince
│
├─ roles
│  └─ ...
│
└─ profile
   ├─ accent
   ├─ guildAvatar
   ├─ globalAvatar
   └─ banner
```

## Tecnologias

- Node.js
- TypeScript
- discord.js
- Sharp
- dotenv
- PM2

## Estrutura

```text
CheckIn/
├── src/
│   └── index.ts
├── .env.example
├── .gitignore
├── package.json
├── package-lock.json
├── tsconfig.json
└── README.md
```

`dist/`, `node_modules/` e `.env` não fazem parte do repositório.

## Instalação

Clone o projeto:

```bash
git clone <URL-DO-REPOSITORIO>
cd CheckIn
```

Instale as dependências:

```bash
npm install
```

## Configuração

Crie um arquivo `.env` na raiz do projeto:

```env
DISCORD_TOKEN=
USER_ID=
CATRACA_CHANNEL_ID=
```

### DISCORD_TOKEN

Token do bot criado no Discord Developer Portal.

Nunca publique esse valor.

### USER_ID

ID do usuário utilizado pelo modo de teste.

### CATRACA_CHANNEL_ID

ID do canal onde os registros do CheckIn serão enviados.

## Discord Developer Portal

O bot utiliza o evento de entrada de membros e precisa do seguinte Privileged Gateway Intent:

```text
Server Members Intent → ON
```

Permissões utilizadas no canal de registros:

```text
View Channels
Send Messages
Embed Links
Manage Messages
```

`Manage Messages` é utilizado pelo modo de reconstrução para remover registros antigos do CheckIn.

## Desenvolvimento

Executar diretamente o projeto TypeScript:

```bash
npm start
```

## Teste

Gera um CheckIn utilizando o usuário definido em `USER_ID`:

```bash
npm run test-checkin
```

## Sincronização

Busca os membros atuais do servidor, ordena pela data de entrada e gera os registros:

```bash
npm run sync-checkin
```

## Reconstrução

Remove registros antigos gerados pelo CheckIn e recria os cards dos membros:

```bash
npm run rebuild-checkin
```

## Build

Compile o TypeScript:

```bash
npx tsc
```

O build é gerado em:

```text
dist/src/index.js
```

Para executar diretamente a versão compilada:

```bash
node ./dist/src/index.js
```

## Produção com PM2

O projeto pode permanecer ativo utilizando PM2:

```bash
pm2 start ./dist/src/index.js --name "CheckIn"
```

Verificar o processo:

```bash
pm2 list
```

Ver logs:

```bash
pm2 logs CheckIn
```

Reiniciar:

```bash
pm2 restart CheckIn
```

Salvar os processos:

```bash
pm2 save
```

## Atualizando o bot

Depois de alterar `src/index.ts`, a versão de produção precisa ser recompilada:

```bash
npx tsc
pm2 restart CheckIn
```

Fluxo:

```text
src/index.ts
     ↓
   npx tsc
     ↓
dist/src/index.js
     ↓
    PM2
     ↓
Discord
```

## Segurança

O arquivo `.env` está incluído no `.gitignore`.

```gitignore
node_modules/
dist/
.env
```

Nunca publique:

- Token do bot
- Credenciais
- Chaves privadas
- Arquivos `.env`

O repositório utiliza `.env.example` apenas para documentar as variáveis necessárias.

## Autor

Desenvolvido por Lucas.