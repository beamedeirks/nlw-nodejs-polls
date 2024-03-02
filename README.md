# NLW - Trilha NodeJS - RocketSeat

Este projeto é uma aplicação de enquetes em tempo real, desenvolvida durante a trilha de Node.js do evento Next Level Week (NLW) da RocketSeat. Utilizando um stack moderno que inclui Node.js, Fastify, WebSocket, Redis, PostgreSQL, e Docker.

## Desenvolvimento

Durante o desenvolvimento, foram aplicados conceitos de API REST utilizando TypeScript e o framework Fastify. A integração do Prisma ORM facilitou a interação com o banco de dados PostgreSQL, enquanto o Docker foi utilizado para lidar com os serviços de PostgreSQL e Redis de forma simplificada.

A validação de dados foi realizada utilizando Zod, garantindo a integridade e consistência dos dados recebidos pela aplicação. Além disso, a comunicação em tempo real foi implementada por meio de WebSocket, permitindo atualizações instantâneas dos resultados das enquetes para os usuários.


## Instalação e Configuração

Para começar a utilizar este projeto, siga os passos abaixo:

1. Execute o comando abaixo para instalar as dependências:
   ```bash
   npm init
   ```
2. Após a instalação das dependências, inicie o projeto com o seguinte comando:
   ```bash
   npm run dev
   ```
3. É necessário que tenha o Docker instalado, caso seja necessário, utilize o Docker Compose para iniciar os containers do Docker:
   ```bash
   docker-compose up -d
   ```

## Routes

### Criação de enquete

**Descrição:** Esta rota permite criar uma nova enquete.

**Método HTTP:** POST

**Endpoint:** `localhost:3333/polls`

**Parâmetros:**
- `title` (string): O título da enquete.
- `options` (array de strings): As opções disponíveis para a enquete.

**Exemplo de requisição:**
```json
{
	"title": "Qual o melhor framework em Node JS?",
	"options": ["Express", "Fastify", "NestJS", "HapiJS"]
}
```
**Exemplo de resposta:**
```json
{
	"pollId": "1154e15c-4861-402a-86f0-c6803fd3f0b2"
}
```

### Criação de voto na enquete

**Descrição:** Esta rota permite criar um voto na enquete.

**Método HTTP:** POST

**Endpoint:** `localhost:3333/polls/:pollId/votes`

**Parâmetros:**
- `pollOptionId` (string): A ID da opção da enquete.

**Exemplo de requisição:**
```json
{
	"pollOptionId":"31572617-0f93-4bd3-8ad6-0b95c12c51c1"
}
```
**Exemplo de resposta (sucesso):**
```json
  // Status: 201 Created
```
**Exemplo de resposta (erro 400):**
```json
{
	"message": "You have already voted on this poll"
}
```
### Buscar enquete

**Descrição:** Esta rota permite buscar uma enquete.

**Método HTTP:** GET

**Endpoint:** `localhost:3333/polls/:pollId`

**Exemplo de resposta:**
```json
{
	"poll": {
		"id": "1154e15c-4861-402a-86f0-c6803fd3f0b2",
		"title": "Qual o melhor framework em Node JS?",
		"options": [
			{
				"id": "4bf46822-8d31-45d6-9042-fac1b90a7413",
				"title": "Express",
				"score": 0
			},
			{
				"id": "1533bd29-9bb2-46ec-8542-082a4e25a9b6",
				"title": "Fastify",
				"score": 0
			},
			{
				"id": "31572617-0f93-4bd3-8ad6-0b95c12c51c1",
				"title": "NestJS",
				"score": 0
			},
			{
				"id": "a4e31b24-169b-4d4f-adee-648c4a96f7ea",
				"title": "HapiJS",
				"score": 1
			}
		]
	}
}
```
### Resultado das enquetes

**Descrição:** Esta rota permite o retorno dos resultados das enquetes utilizando o websocket.

**Método:** WebSocket Request

**Endpoint:** `ws://localhost:3333/polls/:pollId/results`

**Exemplo de resposta:**

A rota WebSocket `ws://localhost:3333/polls/:pollId/results` permite receber atualizações em tempo real dos resultados das enquetes. A resposta é enviada como uma mensagem JSON contendo o ID da opção da enquete e o número de votos correspondente.

**Exemplo de mensagem de resposta:**
```json
  {"pollOptionId":"31572617-0f93-4bd3-8ad6-0b95c12c51c1","votes":1}
  {"pollOptionId":"a4e31b24-169b-4d4f-adee-648c4a96f7ea","votes":0}
```

## Licença

Desenvolvido durante a trilha de Node.js do evento Next Level Week (NLW) da RocketSeat 💜
