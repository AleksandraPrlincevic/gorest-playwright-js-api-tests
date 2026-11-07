# GoRest API Automation with Playwright

## Description
This is a practice project focused on API test automation using Playwright and JavaScript. Previous API testing practice on the same application was done using Postman and Rest Assured. 

The project covers Users and Todos resources of the GoRest API, including positive and negative test scenarios.

## Tech Stack
- JavaScript (Node.js)
- Visual Studio Code
- Playwright Test 1.62.1
- @faker-js/faker 10.6.0
- dotenv 17.4.2

## Prerequisites

- Node.js
- npm
- Visual Studio Code

## Installation

Clone the repository:

```bash
git clone https://github.com/AleksandraPrlincevic/gorest-playwright-js-api-tests.git
```

Navigate to the project directory and install dependencies:

```bash
cd playwright-api-gorest
npm install
```

## Configuration

Create a `.env` file in the project root directory and add your GoRest API token:

```bash
API_TOKEN=your_api_token
```

The base URL and authorization header are already configured in `playwright.config.js`

## How to run tests

Run all tests:

```bash
npx playwright test
```

Open the HTML test report:

```bash
npx playwright show-report
```

## Project Structure

- `tests/`
  - `users.spec.js` - API tests for Users endpoints
  - `todos.spec.js` - API tests for Todos endpoints
- `utils/`
  - `fixtures.js` - Custom Playwright fixtures for creating and cleaning up test data
  - `apiHelper.js` - Reusable API request methods and test data generation functions
  - `endpoints.js` - API endpoint definitions
- `.env` - Stores the API authentication token (see [Configuration](#configuration))
- `playwright.config.js` - Playwright configuration
- `package.json` - Project dependencies and metadata
- `package-lock.json` - Records the exact dependency versions and their dependencies
- `.gitignore` - Specifies files and directories ignored by Git. Contains `.env` and `node_modules`
- `README.md`

## Framework overview
- **API Testing:** Uses Playwrights `APIRequestContext` to send HTTP requests directly to the API.
- **Test Data Management:**
  - **Custom Fixtures:** Extends Playwright base tests with `userFixture` and `todoFixture` for test data setup and teardown
  - **Faker:** generateS dynamic test data
- **Reusable API Helper:** Separates API request methods and test data generation from test implementation
- **Configuration:** Uses an environment variable for API authentication. The base URL is configured in `playwright.config.js`, while API endpoints are defined in `endpoints.js`

## What's covered
**Users:**
- CRUD operations (GET, POST, PUT, PATCH, DELETE)
- Positive and negative test scenarios
- Retrieving all users and individual users
- Creating users and validating duplicate email errors
- Updating individual user fields and replacing existing user resources
- Deleting users and verifying their removal through subsequent GET requests

**Todos:**
- Retrieving all todos and todos belonging to a specific user
- Creating todos directly and through the user endpoint
- Updating todo status using PATCH
- Deleting todos and verifying their removal
- Negative scenarios covering missing required properties, invalid user IDs, invalid status values and invalid todo IDs

**Response Validation:**
- HTTP status codes
- Response body structure and resource properties
- Data consistency after POST, PUT and PATCH operations
- API validation error messages
- Resource existance and removal verified through subsequent GET request  
