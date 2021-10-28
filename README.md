# Desafio 2 do Ignite Trilha NodeJS

<img alt="Ignite" src="./assets/cover-node.js.png" />

<h3 align="center">
  Chapter 02: Introdução ao SOLID e Documentação com Swagger
</h3>

<p align="center">“Nunca se compare com ninguém neste mundo. Caso o faça, entenda que você estará insultando a si mesmo”</blockquote>

<p align="center">
  <img alt="GitHub top language" src="https://img.shields.io/github/languages/top/TainaIsabela/Ignite-Node-Desafio-1?style=flat">

  <a href="https://rocketseat.com.br">
    <img alt="Made by Tainá Isabela" src="https://img.shields.io/badge/made%20by-Tainá%20Isabela-orange">
  </a>

  <img alt="License" src="https://img.shields.io/badge/license-MIT-%2304D361">

  <a href="https://github.com/rocketseat-education/ignite-template-trabalhando-com-middlewares/stargazers">
    <img alt="Stargazers" src="https://img.shields.io/github/stars/rocketseat-education/ignite-template-trabalhando-com-middlewares?style=social">
  </a>
</p>


<p align="center">
  <a href="#rocket-sobre-o-desafio">Sobre o desafio</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#keyboard-instalação-e-execução-do-projeto">Instalação e Execução do Projeto</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#template-da-aplicação">Template da aplicação</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#rotas-da-aplicação">Rotas da aplicação</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#especificação-dos-testes">Específicação dos testes</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#Testes-das-rotas">Testes-das-rotas</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#memo-licença">Licença</a>
</p>

## :rocket: Sobre o desafio

Essa será uma aplicação de listagem e cadastro de usuários. Para que a listagem de usuários funcione, o usuário que solicita a listagem deve ser um admin (mais detalhes ao longo da descrição). Utilizando essa aplicação já funcional como base, realizei a documentação das rotas com o Swagger.

### :keyboard: Instalação e Execução do Projeto

- Clone este repositório

```
> git clone https://github.com/TainaIsabela/Ignite-Node-Desafio-2
```

- Navegue até o diretório principal do projeto

```
> cd Ignite-Middlewares
```

- Instale as dependências com o Yarn

```
yarn
```

- Rode a suite de testes

```
yarn test
```

- Execute o projeto

```
yarn dev
```


### Template da aplicação

Foi utilizado um modelo de template que possui o esqueleto do projeto.

O template pode ser encontrado na seguinte url: **[Acessar Template](https://github.com/rocketseat-education/ignite-template-introducao-ao-SOLID)**

> **Dica**: Caso não saiba utilizar repositórios do Github como template, utilize o guia em **[nosso FAQ](https://www.notion.so/ddd8fcdf2339436a816a0d9e45767664).**

Agora navegue até a pasta criada e abra no Visual Studio Code, lembre-se de executar o comando `yarn` no seu terminal para instalar todas as dependências.

### Rotas da aplicação


#### **POST/users**

A rota deve receber name, e email dentro do corpo da requisição para que seja possível cadastrar um usuário.


#### **PATCH /users/:user_id/admin**

A rota deve receber name, e email dentro do corpo da requisição para que seja possível cadastrar um usuário.

#### **GET /users/:user_id/admin**

A rota deve receber, nos parâmetros da rota, o id de um usuário e devolver as informações do usuário encontrado pelo corpo da resposta.
#### **GET /users/**

A rota deve receber, pelo header da requisição, uma propriedade user_id contendo o id do usuário e retornar uma lista com todos os usuários cadastrados. O id deverá ser usado para validar se o usuário que está solicitando a listagem é um admin. O retorno da lista deve ser feito apenas se o usuário for admin. 

## Especificação dos testes

Em cada teste, tem uma breve descrição no que sua aplicação deve cumprir para que o teste passe.
Para esse desafio, temos os seguintes testes:

## Testes do model

- **Should be able to create an user with all props**

    Para que esse teste passe, você deve completar o código do model de usuários que está em src/modules/users/model/User.ts. O usuário deve ter as seguintes propriedades:

```
{
  id: string;

  name: string;

  admin: boolean;

  email: string;

  created_at: Date;

  updated_at: Date;
}
```
    
## Testes do repositório
- **Should be able to create new users**

    Para que esse teste passe, é necessário que o método create do arquivo src/modules/users/repositories/implementations/UsersRepository permita receber o name e email de um usuário, crie um usuário a partir do model (que foi completado no teste anterior).

- **Should be able to list all users**

    Para que esse teste passe, é necessário que o método list do arquivo src/modules/users/repositories/implementations/UsersRepository retorne a lista de todos os usuários cadastrados na aplicação.

- **Should be able to find user by ID**

    Para que esse teste passe, é necessário que o método findByEmail do arquivo src/modules/users/repositories/implementations/UsersRepository receba o email de um usuário e retorne o usuário que possui o mesmo email.

- **Should be able to turn an user as admin**

    Para que esse teste passe, é necessário que o método turnAdmin do arquivo src/modules/users/repositories/implementations/UsersRepository receba o objeto do usuário completo, mude a propriedade admin para true, atualize também a propriedade updated_at  e retorne o usuário atualizado.



## Testes de useCases


- **Should be able to create new users**

    Para que esse teste passe, é necessário que o método `execute` do arquivo **src/modules/users/useCases/createUser/CreateUserUseCase.ts** receba `name` e `email` do usuário a ser criado, crie o usuário através do método `create` do repositório e retorne o usuário criado.

- **Should not be able to create new users when email is already taken**

    Para que esse teste passe, é necessário que o método `execute` do arquivo **src/modules/users/useCases/createUser/CreateUserUseCase.ts** não permita que um usuário seja criado caso já exista um usuário com o mesmo email e, nesse caso, lance um erro no seguinte formato:

    ```
    throw new Error("Mensagem do erro");
    ```


- **Should be able to turn an user as admin**

    Para que esse teste passe, é necessário que o método execute do arquivo src/modules/users/useCases/turnUserAdmin/TurnUserAdminUseCase.ts receba o id de um usuário, chame o método do repositório que transforma esse usuário em administrador e retorne o usuário após a alteração.

- **Should not be able to turn a non existing user as admin**

    Para que esse teste passe, é necessário que o método execute do arquivo src/modules/users/useCases/turnUserAdmin/TurnUserAdminUseCase.ts não permita que um usuário que não existe seja transformado em admin. Caso o usuário não exista, lance um erro no seguinte formato:

    ```
    throw new Error("Mensagem do erro");
    ```

- **Should be able to get user profile by ID**

   Para que esse teste passe, é necessário que o método execute do arquivo src/modules/users/useCases/showUserProfile/ShowUserProfileUseCase.ts receba o id de um usuário, chame o método do repositório que busca um usuário pelo id e retorne o usuário encontrado.

- **Should not be able to show profile of a non existing user**

  Para que esse teste passe, é necessário que o método execute do arquivo src/modules/users/useCases/showUserProfile/ShowUserProfileUseCase.ts não permita que um usuário que não existe seja retornado. Caso o usuário não exista, lance um erro no seguinte formato:

  ```
    throw new Error("Mensagem do erro");
  ```
- **Should be able to list all users**

   Para que esse teste passe, é necessário que o método execute do arquivo src/modules/users/useCases/listAllUsers/ListAllUsersUseCase.ts chame o método do repositório que retorna todos os usuários cadastrados e retorne essa informação.

- **Should not be able to a non admin user get list of all users**

  Para que esse teste passe, é necessário que o método execute do arquivo src/modules/users/useCases/listAllUsers/ListAllUsersUseCase.ts receba o id de um usuário e retorne a listagem de usuários cadastrados na aplicação apenas se o id recebido pertencer a um usuário admin.
  Caso o usuário não seja admin, lance um erro no seguinte formato:

  ```
    throw new Error("Mensagem do erro");
  ```

- **Should not be able to a non existing user get list of all users**

  Para que esse teste passe, é necessário que o método execute do arquivo src/modules/users/useCases/listAllUsers/ListAllUsersUseCase.ts não permita que um usuário que não exista, acesse a listagem de usuários cadastrados na aplicação. Caso o usuário não exista, lance um erro no seguinte formato:

  ```
    throw new Error("Mensagem do erro");
  ```



Todos os demais testes são os mesmos testes encontrados no desafio 01 com algumas (ou nenhuma) mudanças.

>  :warning: Vale reforçar que esse desafio é focado apenas em middlewares e você não precisa modificar o conteúdo das rotas para que os testes passem 💜

## :memo: Licença

Esse projeto está sob a licença MIT. Veja o arquivo [LICENSE](https://github.com/git/git-scm.com/blob/master/MIT-LICENSE.txt) para mais detalhes.

---

Feito com 💜 by <a href="https://www.linkedin.com/in/taina-isabela">Tainá Isabela</a> :wave:
