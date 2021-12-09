# Sistema do CEIP-USP

## O CEIP-USP

CEIP-USP é o Centro-Escola do Instituto de Psicologia da USP. Suas atividades giram em torno de prover atividades para o bem tanto da comunidade USP, quanto da comunidade externa. Tais atividades estão sob as responsabilidades dos Serviços e envolvem diversos profissionais, bem como outros responsáveis. Todo o Centro-Escola é gerenciado por um Supervisor-Geral.

Por conta da pandemia do novo coronavirus, algumas medidas de controle se fizeram necessárias. Para este fim, está em desenvolvimento o sistema de acesso às dependências do CEIP. O intuito da aplicação é, primordialmente, garantir a segurança e a saúde de todos que circulam no prédio, através do cadastramento dos mesmos. Com tal cadastro, fica facilitada a instrução e o encaminhamento de pessoas externas.


## O sistema

O sistema consiste em uma aplicação Web, composta por três partes:

  1. um _**frontend**_, feito em ReactJS, escrito em TypeScript - [saiba mais][front]
  2. um _**backend**_, feito em ExpressJS, escrito em TypeScript - [saiba mais][back]
  3. um **banco de dados** MongoDB, que segue o modelo de Documentos - [saiba mais][db]

Cada uma das partes do sistema está implementada em um Contêiner Docker diferente. A imagem a seguir apresenta uma visão estrutural dos contêineres, suas interações e as tecnologias adotadas internamente em cada um.

![visão macro da arquitetura][macro]


## Executando o sistema

Para executar o sistema como um todo, é necessário somente executar os contêineres da aplicação. Veja mais especificidades nas páginas do [Frontend][front] e do [Backend][back], nas respectivas seções **Executando em Desenvolvimento**.


[front]: ./frontend
[back]: ./backend
[db]: https://www.mongodb.com
[macro]: ./macro.png
