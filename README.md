# Documentação da API Fintera - Recebíveis

## Desenvolvimento

### Setup

O projeto utiliza [Docker](https://www.docker.com/), sendo ele a única dependência.

Para rodar a documentação basta executar o comando abaixo, que realizará o build da documentação e iniciar o servidor:

```sh
docker-compose up -d
```

Você poderá acessar a documentação localmente no endereço: http://localhost:4567

### Atualizar o Slate

Por usarmos o Slate dentro do container Docker para "buildar" e rodar o projeto, toda atualização dele, deve ser feita atualizando a versão da [imagem oficial do Slate](https://hub.docker.com/r/slatedocs/slate/tags) no `docker-compose.yml`. Sendo recomendado configurar uma versão específica, para termos controle de qual versão estamos usando. Maiores detalhes sobre o uso Slate com Docker estão na [Wiki do Slate](https://github.com/slatedocs/slate/wiki/Using-Slate-in-Docker).


## Deploy

Estamos usando o GitHub Actions como CD e o GitHub Pages como hospedagem.

A configuração do workflow de CD está no [deploy.yml](https://github.com/Myfc-github/receivables-api-docs/blob/main/.github/workflows/deploy.yml), onde cada passo está comentado para facilitar o entendimento.

O deploy é realizado automaticamente, sempre que a branch `main` é atualizada, e a documentação fica acessível no endereço [api-docs.recebiveis.fintera.com.br](https://api-docs.recebiveis.fintera.com.br/).

