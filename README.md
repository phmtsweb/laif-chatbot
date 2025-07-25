# Damiana Rasa Chatbot

Este projeto é um chatbot desenvolvido com o framework [Rasa](https://rasa.com/), preparado para ser executado e treinado facilmente utilizando Docker Compose.

## Pré-requisitos

- [Docker](https://www.docker.com/get-started) 
- [Docker Compose](https://docs.docker.com/compose/) 

## Estrutura do Projeto

- `actions/`: Ações customizadas em Python
- `data/`: Dados de treinamento (NLU, histórias, regras)
- `models/`: Modelos treinados
- `domain.yml`: Domínio do bot
- `docker-compose.yml`: Orquestração dos serviços

## Como executar o projeto

### 1. Treinamento do modelo

Para treinar o modelo Rasa, execute:

```sh
docker compose run --rm rasa train
```

O modelo treinado será salvo na pasta `models/`.

### 2. Subir o chatbot

Após o treinamento, inicie o bot e o servidor de ações customizadas:

```sh
docker compose up -d --build
```

- O Rasa estará disponível em `http://localhost:5005`
- O servidor de ações estará disponível em `http://localhost:5055`
- O chatbot web estará disponível em `http://localhost:3000`

### 3. Conversar com o bot

Você pode conversar com o bot via terminal:

```sh
docker compose run rasa shell
```

Ou integrar com outros canais suportados pelo Rasa.

### 4. Gerar o fluxograma de conversas

Para gerar o fluxograma (em formato HTML), execute:

```sh
docker compose run rasa visualize --max-history 5 --output graph.html
```

O arquivo `graph.html` será gerado na raiz do projeto e pode ser aberto em qualquer navegador.

## Observações

- Sempre que alterar arquivos de treinamento (`data/`, `domain.yml`), é necessário treinar novamente o modelo.
- Para parar os serviços:

```sh
docker compose down
```

## Referências

- [Documentação Rasa](https://rasa.com/docs/)
- [Documentação Docker Compose](https://docs.docker.com/compose/)
