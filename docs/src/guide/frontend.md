# Frontend

[[TOC]]

O frontend tem por responsabilidade cuidar da interface de usuário, por meio de uma aplicação Web.

A biblioteca [ReactJS][react] auxilia na criação dos componentes estruturais, juntamente com a linguagem [TypeScript][ts] para a escrita dos arquivos. Os aspectos de estilo são definidos usando [TailwindCSS][tailwind], um framework de CSS com abordagem funcional. A responsável por fazer as requisições para o backend é a biblioteca [Axios][axios].

## A estrutura

A aplicação está dividida entre alguns elementos diferentes:

- **componentes** - representam uma parte do layout;
- **páginas** - são especializações de componentes, com o propósito de representar uma visualização composta por componentes, mapeada para uma rota do site;
- **contextos** - agrupam informações em um estado para ser compartilhado entre componentes;
- **hooks** - são operações que podem ser utilizadas por outros hooks e por componentes; eventualmente fazem uso de um ou mais contextos.

A image ilustra a relação entre os elementos.

![elementos do frontend][elements]

A implementação dos **componentes** seguiu um padrão chamado de "Dumb Components & Smart Objects". Quando você precisa desenvolver uma aplicação frontend que prese por testabilidade, torna-se complexo criar testes de unidade em componentes visuais. Para isso, você pode adotar o padrão "Dumb Components & Smart Objects" que propõe a separação entre a estrutura visual e a estrutura lógica de um componente. A parte lógica é implementada em um objeto chamado Smart Object, para o qual é fácil escrever testes de unidade. A estrutura visual é implementada em um Dumb Component, que delega a lógica para o seu correspondente Smart Object.

## A conteinerização

O frontend conta com alguns arquivos que gerenciam a conteinerização da aplicação:
- [Dockerfile][dockerfile]
- [Docker-Compose][docker-compose]
- `.env` que segue a estrutura descrita no [.env.sample][env-sample]

Este contêiner tem um processo que serve a aplicação para ser executada em um navegador. É importante que a aplicação tenha acesso ao endereço onde encontra-se o backend. Para isso, existe a definição da variável de ambiente `REACT_APP_BACKEND_URL`.

## Execução em Desenvolvimento

Para subir o servidor de backend, é importante garantir que o `.env` tenha preenchido todas as variáveis. Caso você tenha interesse em integrar com o backend próprio, veja mais [na página do backend][back]. Caso esteja substituindo o backend com outra ferramenta, preencha `REACT_APP_BACKEND_URL` com o endereço do substituto.
Depois disso, basta criar os contêineres:

```bash
docker compose up --build
```

Este comando criará dois contêineres: um com uma instância de MongoDB, outro com o backend em desenvolvimento.


## Ambiente de Produção

O [_deploy_ do frontend][deploy] está no [Netlify][netlify], uma plataforma de hospedagem de sites estáticos. O _deploy_ é feito de maneira automática a cada novo _commit_ na _branch main_ do repositório. Além disso, a cada _pull request (PR)_, uma previsualização do _deploy_ é gerada e fica disponível.

[react]: https://reactjs.org
[ts]: https://www.typescriptlang.org
[tailwind]: https://tailwindcss.com
[axios]: https://axios-http.com

[elements]: ./front-elements.png

[dockerfile]: https://github.com/CEIP-USP/frontend/blob/main/Dockerfile
[docker-compose]: https://github.com/CEIP-USP/frontend/blob/main/docker-compose.yaml
[env-sample]: https://github.com/CEIP-USP/frontend/blob/main/.env.sample

[back]: ./backend

[deploy]: https://ceip-usp.netlify.app
[netlify]: https://www.netlify.com
