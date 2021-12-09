# Backend

O backend tem por responsabilidade cuidar da estrutura lógica e da persistência de dados, expondo operações via API HTTP REST.

A biblioteca [ExpressJS][express] auxilia na criação da API REST, que está implementada usando a linguagem [TypeScript][ts]. O acesso ao banco de dados é feito pelo [cliente do MongoBD puro][mongodb].

## A estrutura

A aplicação está dividida entre alguns elementos diferentes:

- **controladores**: responsáveis por interagir com requisições e respostas;
- **casos de uso**: implementa as ações do lógica da aplicação;
- **repositórios**: oferece ações sobre o agregado de dados;
- **entidades**: modela noções do mundo real na aplicação.

A imagem ilustra a relação entre os elementos.

![Elementos do Backend][back]

## A conteinerização

O backend conta com alguns arquivos que gerenciam a conteinerização da aplicação:

- [Dockerfile][dockerfile]
- [Docker-Compose][compose]
- `.env` que segue a estrutura descrita no [.env.sample][envsample]

::: warning Importante
A variável `JWT_SECRET` é a chave de criação das assinaturas nos tokens JWT e seu valor **não deve ser versionado**
:::




[express]: https://expressjs.com
[ts]: typescriptlang.org/
[mongodb]: https://docs.mongodb.com/drivers/node/current/

[back]: ./back-elements.png

[dockerfile]: https://github.com/CEIP-USP/backend/blob/main/Dockerfile
[compose]: https://github.com/CEIP-USP/backend/blob/main/docker-compose.yaml
[envsample]: https://github.com/CEIP-USP/backend/blob/main/.env.sample
