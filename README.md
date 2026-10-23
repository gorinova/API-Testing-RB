# Restful Booker API Tests

[![Newman API Tests](https://github.com/gorinova/API-Testing-RB/actions/workflows/newman-tests.yml/badge.svg)](https://github.com/gorinova/API-Testing-RB/actions/workflows/newman-tests.yml)

Automated API tests for the [Restful Booker](https://restful-booker.herokuapp.com/) demo service, built in Postman and run with Newman in GitHub Actions on every push.

## What is tested

- **CRUD operations**: create, read, update (PUT and PATCH) and delete bookings
- **Authentication**: token creation and using the token for protected requests
- **Dynamic data**: booking IDs captured from responses and reused in later requests
- **Negative and security tests**: invalid input, missing or invalid tokens, unauthorized actions
- **Query parameters**: filtering bookings
- **Headers and OPTIONS**: checking response headers and allowed methods

**Latest run:** 60 requests, 32 assertions, 0 failed.

## Project structure

```
.github/workflows/newman-tests.yml   CI workflow
postman/collection.json              Postman collection
postman/environment.json             Postman environment (base URL and variables)
postman/package.json                 Newman and htmlextra reporter dependencies
```

## Run locally

Requirements: Node.js 20 or newer.

```
cd postman
npm install
cd ..
npx --prefix postman newman run postman/collection.json -e postman/environment.json -r cli,htmlextra --reporter-htmlextra-export reports/report.html
```

Open `reports/report.html` in your browser to see the detailed report.

## Continuous integration

The GitHub Actions workflow runs on every push:

1. Checks out the repository and sets up Node.js
2. Installs dependencies
3. Runs the collection with Newman
4. Uploads the HTML report as the `newman-html-report` artifact

To view the report, open a workflow run, scroll to **Artifacts**, download `newman-html-report`, and open `report.html`.

## Findings

Add the notable behaviors or bugs you found while testing here, for example unexpected status codes, missing validation, or inconsistent responses.

| # | Endpoint | Expected | Actual | Notes |
|---|----------|----------|--------|-------|
| 1 |          |          |        |       |

## Tools

Postman, Newman, newman-reporter-htmlextra, GitHub Actions