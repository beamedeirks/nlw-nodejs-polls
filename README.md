# Meu Projeto

Um projeto incrível para demonstrar como documentar rotas em um README do GitHub.

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

### Rota 2

Descrição, método HTTP, endpoint, parâmetros, exemplos de requisição e resposta...

## Exemplos

Exemplos práticos de uso das rotas...

## Contribuição

Instruções para contribuir com o projeto...

## Licença

Licença do projeto...
