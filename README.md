# Meu Projeto

Um projeto incrível para demonstrar como documentar rotas em um README do GitHub.

## Instalação e Configuração

Instruções de instalação e configuração...

## Uso

### Rota de criação de enquete

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

**Exemplo de resposta:**
```json
{
	"pollId": "1154e15c-4861-402a-86f0-c6803fd3f0b2"
}


### Rota 2

Descrição, método HTTP, endpoint, parâmetros, exemplos de requisição e resposta...

## Exemplos

Exemplos práticos de uso das rotas...

## Contribuição

Instruções para contribuir com o projeto...

## Licença

Licença do projeto...
