![Screen Shot 2020-06-24 at 14 40 26](https://user-images.githubusercontent.com/54912285/85605620-b59af580-b628-11ea-9c7a-f318a42dbba3.png)


<blockquote align="center">“Para quem fica melhor a cada dia, ficar pronto é utopia”!</blockquote>


<h1 align="center">
  🚀 Conceitos Node.js + Typescript 🚀
</h1>

#### If you need support with the content, go to my [Notion notes](https://www.notion.so/S02-Primeiro-projeto-com-Node-js-7c19011879e245af93fec8667b479b3c)
  
## 🚀 Desafio 05 
O objetivo desse desafio é criar uma aplicação para continuar treinando o que foi aprendido até agora no Node.js junto ao TypeScript, utilizando o conceito de models, repositories e services! Levando em consideração também, alguns dos princípios **SOLID**.

##  🤓 Conceitos importantes
### Model
É uma forma de armazenar os dados, e com isso começar a isolar um pouco as responsabilidades da aplicação.
Os models/entidades vão definir qual é o formato desse dado. 
Todas vez que estivermos *criando algum dado* que vai ser armazenado na nossa aplicação, seja em banco de dados, ou na memória, devemos criar um **model**.

### Repositório
O próximo conceito aplicado dentro do código para melhorar ainda mais a **estrutura e organização** dos arquivos é o conceito de **repositório**.

Podemos pensar por enquanto em repositório como uma relação entre a **persistência** dos dados e a nossa **rota**. 

**Persistência ↔ Repositório ↔ Rota**

Dentro do repositório é onde vou conseguir manipular as **informações que estão persistidas** por exemplo dentro de um banco ou uma variável, com os métodos: *create, all, delete...*


### Services
Um dos conceitos mais importantes da arquitetura de software.

Armazena as regras de negócio da aplicação evitando que as rotas fiquem com responsabilidades demais, o que vai contra ao princípio **SOLID - Single Responsibility Principle (separation of concerns)**. 

A rota deve ficar preocupada com apenas uma coisa: receber a requisição, chamar outro arquivo para tratar essa requisição, e devolver uma resposta. Sempre que tivermos algo além disso, devemos abstrair dentro de um service. 

Dentro do service aplicamos outro princípio chamado SOLID chamado **Dependency Inversion**. Sempre que o service tiver uma dependência externa ao invés de instanciar a classe de repositório dentro do service, nós vamos receber esse repository como um parâmetro da classe no constructor. Isso vai facilitar para que a aplicação independente de quantos services estejam trabalhando com um mesmo repositório, todos eles estejam trabalhando com o mesmo e não repositórios diferentes criados em cada um dos services. 

## :wrench: Funcionalidades da aplicação

Verificar os arquivos da pasta `src` e completar onde não possui código com o código para atingir os objetivos de cada rota.

- **`POST /transactions`**: A rota deve receber `title`, `value` e `type` dentro do corpo da requisição, sendo `type` o tipo da transação, que deve ser `income` para entradas (depósitos) e `outcome` para saídas (retiradas). Ao cadastrar uma nova transação, ela deve ser armazenada dentro de um objeto com o seguinte formato :

```json
{
  "id": "uuid",
  "title": "Salário",
  "value": 3000,
  "type": "income"
}
```

- **`GET /transactions`**: Essa rota deve retornar uma listagem com todas as transações que você cadastrou até agora, junto com o valor de soma de entradas, retiradas e total de crédito. Essa rota deve retornar um objeto com o formato a seguir:

```json
{
  "transactions": [
    {
      "id": "uuid",
      "title": "Salário",
      "value": 4000,
      "type": "income"
    },
    {
      "id": "uuid",
      "title": "Freela",
      "value": 2000,
      "type": "income"
    },
    {
      "id": "uuid",
      "title": "Pagamento da fatura",
      "value": 4000,
      "type": "outcome"
    },
    {
      "id": "uuid",
      "title": "Cadeira Gamer",
      "value": 1200,
      "type": "outcome"
    }
  ],
  "balance": {
    "income": 6000,
    "outcome": 5200,
    "total": 800
  }
}
```

## :warning: Especificação dos testes

Em cada teste, tem uma breve descrição no que sua aplicação deve cumprir para que o teste passe.

Caso você tenha dúvidas quanto ao que são os testes, e como interpretá-los, dé uma olhada em **[nosso FAQ](https://github.com/Rocketseat/bootcamp-gostack-desafios/tree/master/faq-desafios).**

Para esse desafio temos os seguintes testes:

- **`should be able to create a new transaction`**: Para que esse teste passe, sua aplicação deve permitir que uma transação seja criada, e retorne um json com a transação criada.

- **`should be able to list the transactions`**: Para que esse teste passe, sua aplicação deve permitir que seja retornado um objeto contendo todas as transações junto ao balanço de income, outcome e total das transações que foram criadas até o momento.

- **`should not be able to create outcome transaction without a valid balance`**: Para que esse teste passe, sua aplicação não deve permitir que uma transação do tipo `outcome` extrapole o valor total que o usuário tem em caixa, retornando uma resposta com código HTTP 400 e uma mensagem de erro no seguinte formato: `{ error: string }`


***

<h4 align="center">
    Made with :coffee: and 💜 by <a href="https://www.linkedin.com/in/nykollemalone/" target="_blank">Nykolle Malone</a>
</h4>

