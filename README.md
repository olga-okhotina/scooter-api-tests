# Yandex Scooter — API Test Automation

Automated API tests for the [Yandex Scooter](https://qa-scooter.praktikum-services.ru) backend.

## Tech stack
Java 11 · REST Assured · JUnit 5 · Allure · Maven

## Test coverage
| Area | Scenarios |
|---|---|
| Create courier | success, `ok: true` response, duplicate courier, existing login, missing login, missing password |
| Courier login | success returns `id`, missing login, missing password, wrong login, wrong password, non-existent courier |
| Create order | parameterized by scooter color: BLACK, GREY, both, none |
| Orders list | response contains a list of orders |

## Architecture
- **Client layer** — base `Client` with shared request spec; `CourierClient`, `OrderClient` per API domain
- **Checker classes** — response assertions separated from test logic
- **Test data cleanup** — couriers are deleted and orders cancelled after each test
- **Allure** reports with request/response logging

## Run tests
mvn clean test
mvn allure:serve
