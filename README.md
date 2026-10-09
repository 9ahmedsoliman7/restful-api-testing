# RESTful API Testing (Postman + Newman)

An automated API test suite for the public [Restful API](https://api.restful-api.dev) service, built with **Postman**. It covers the full CRUD cycle (GET, POST, PUT, PATCH, DELETE) with JavaScript assertions, chained requests, JSON schema validation and a negative test, and it can run from the command line with **Newman**.

## Tech stack

| Area | Tool |
|---|---|
| API client | Postman |
| Command-line runner | Newman |
| Protocol / format | HTTP, REST, JSON |
| Assertions | Postman test scripts (JavaScript, Chai) |

## Requests in the collection

The requests run in this order, because later ones reuse the `id` created by the first POST.

| # | Request | Method | Endpoint |
|---|---|---|---|
| 1 | objects list | GET | `/objects` |
| 2 | single object | GET | `/objects/7` |
| 3 | add a new object | POST | `/objects` |
| 4 | update an object | PUT | `/objects/{{objectId}}` |
| 5 | partially update an object | PATCH | `/objects/{{objectId}}` |
| 6 | new object | POST | `/objects` |
| 7 | delete an object | DELETE | `/objects/{{objectId}}` |
| 8 | GET deleted object | GET | `/objects/{{objectId}}` |

## What is tested

- **Status codes** for every request.
- **Response time** below 1000 ms.
- **Response body:** field values, data types, and that the object `id` stays the same after PUT and PATCH.
- **JSON schema validation** on the single-object response.
- **Negative test:** a deleted object is no longer found (404).
- **Request chaining:** the POST test saves the new object's `id` in the collection variable `objectId`, and PUT, PATCH, DELETE and the final GET use it.

## Variables

| Variable | Where | Purpose |
|---|---|---|
| `baseUrl` | Collection variable | `https://api.restful-api.dev` |
| `objectId` | Collection variable | Filled automatically by the POST test |
| `apiKey` | Postman **Environment** | Needed for the DELETE request |

The API key is **not stored in this repository**. Create your own environment with an `apiKey` variable.

## How to run

### In Postman

1. Import `restful.postman_collection.json`.
2. Create an Environment with a variable named `apiKey` and your own key, then select that environment.
3. Open the collection and click **Run**.

### With Newman

```
npm install -g newman
newman run restful.postman_collection.json --env-var "apiKey=YOUR_API_KEY"
```

## Author

**Ahmed Soliman**, Junior QA Engineer (ISTQB CTFL)

- LinkedIn: [linkedin.com/in/ahmed-soliman-qa](https://linkedin.com/in/ahmed-soliman-qa)
- GitHub: [github.com/9ahmedsoliman7](https://github.com/9ahmedsoliman7)
