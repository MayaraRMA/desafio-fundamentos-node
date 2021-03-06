# desafio-fundamentos-node
- POST /transactions: A rota recebe title, value e type dentro do corpo da requisição, sendo type o tipo da transação, que deve ser income para entradas (depósitos) e outcome para saidas (retiradas). Ao cadastrar uma nova transação, ela deve ser armazenada dentro de um objeto com o formato como o seguinte:
```
{
  "id": "uuid",
  "title": "Salário",
  "value": 3000,
  "type": "income"
}
```

- GET /transactions: Essa rota retorna uma listagem com todas as transações que você cadastrou até agora, junto com o valor de soma de entradas, retiradas e total de crédito. Essa rota deve retornar um objeto com o formato a seguir:

```
  {
  "transactions":
    [
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
  "balance":
    {
      "income": 6000,
      "outcome": 5200,
      "total": 800
    }
  }
```


## testes:

- should be able to create a new transaction: a aplicação deve permitir que uma transação seja criada, e retorne um json com a transação criado.

- should be able to list the transactions: a aplicação deve permitir que seja retornado um objeto contendo todas as transações junto ao balanço de income, outcome e total das transações que foram criadas até o momento.

- should not be able to create outcome transaction without a valid balance: a aplicação não deve permitir que uma transação do tipo outcome extrapole o valor total que o usuário tem em caixa, retornando uma resposta com código HTTP 400 e uma mensagem de erro no seguinte formato: { error: string }
