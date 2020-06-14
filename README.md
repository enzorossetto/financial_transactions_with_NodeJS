# Create Income and Outcome transactions - application done with NodeJS

## To run the project

1. You must have [NodeJS](https://nodejs.org/en/download/) on your machine
   - And [Yarn](https://classic.yarnpkg.com/en/docs/install) if you want to run without modifying any file

2. Open the project folder in your terminal and run the command `yarn` to install the dependencies
   - Or run `npm i` if not using yarn

3. Run the command `yarn dev:server` to start the application
   - You may have to change the `scripts` inside [package.json](https://github.com/enzorossetto/financial_transactions_with_NodeJS/blob/master/package.json)

## Routes

> The base URL is **http://localhost:3333**

> Use something like [Insomnia](https://insomnia.rest/download/) to make the requests

- `POST /transactions`: you must pass JSON as body with the fields `title`, `value` and `type` to this route
  - _title_ must be a string
  - _value_ must be a number
  - _type_ must be `income` or `outcome`
  - You can't create an outcome that is higher than your total
  - The response will be something like

        {
          "id": "uuid",
          "title": "Salário",
          "value": 3000,
          "type": "income"
        }

- `GET /transactions`: this route will return all your transactions and your balance as a JSON like:

      {
        "transactions": [
          {
            "id": "uuid",
            "title": "Salary",
            "value": 4000,
            "type": "income"
          },
          {
            "id": "uuid",
            "title": "Freelance",
            "value": 2000,
            "type": "income"
          },
          {
            "id": "uuid",
            "title": "Invoice payment",
            "value": 4000,
            "type": "outcome"
          },
          {
            "id": "uuid",
            "title": "Gamer chair",
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
      
      
 > For now there are only two routes. In futere there may be more
