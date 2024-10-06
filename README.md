# FoodySoftUniExam---API-Automation-Testing
This repository contains automated API tests for the FoodySoftUni application. The tests are built and executed using Postman.

## Table of Contents

- Project Overview
- Setup and Installation
- Test Cases
- Running the Tests
- Collection Structure
- Scripts
- Contributing
- License
  
## Project Overview
This project tests various endpoints of the FoodySoftUniExam API. The functionalities covered include authentication, food creation, editing, searching, and deletion. These API tests ensure that the main features of the application work as expected.

## Setup and Installation
1. ### Clone the repository:

git clone https://github.com/yourusername/FoodySoftUniExam.git

2. ### Install Postman: Download and install Postman if you don't have it already.

3. ### Import Collection:

- Open Postman.
- Go to File > Import and select the Postman collection JSON file from this repository.
  
4. ### Set Up Environment Variables: Create the following environment variables in Postman:

- baseURL: The base URL for API requests.
- token: The access token for authentication.
  
## Test Cases
## 1. Authentication
### Endpoint: POST /api/User/Authentication
Tests for:

- Status code is 200.
- Response body contains username, password, and accessToken.
- Token is stored in a collection variable for use in other requests.
  
## 2. Create New Food
### Endpoint: POST /api/Food/Create
Tests for:

- Successful creation of a food item.
- Verifies that the response contains the correct food attributes.
## 3. Search for Food
### Endpoint: GET /api/Food/Search
Tests for:

- Searching and returning the correct food item.

## 4. Edit the Food Name
### Endpoint: PATCH /api/Food/Edit/{id}
Tests for:

- Updating the food item's name.
- Verifies the change through a subsequent GET request.

## 5. Delete the Edited Food
### Endpoint: DELETE /api/Food/Delete/{id}
Tests for:

- Successful deletion of the edited food.
  
## Running the Tests
To run the tests, follow these steps:

1. Open Postman.
2. Run the imported Postman collection.
3. Verify the results in the Tests tab for each request.
   
## Collection Structure
The collection is structured as follows:

### - Authenticate and set Access Token: Handles user login and stores the token.
### - Create new food: Adds a new food item.
### - Search for food: Retrieves food based on search criteria.
### - Edit the name of the food: Modifies the name of a previously created food item.
### - Delete the Edited Food: Deletes the modified food item.

## Scripts
Postman scripts are used for verifying API responses and handling dynamic data. For example:

### - Post-Response Scripts: Verifies that the status code is 200, checks that the response body contains specific fields, and saves the access token for reuse.

pm.test("Code is 200", function () {
  pm.response.to.have.status(200);
});

pm.test("Response body has correct props", () => {
  const jsonData = pm.response.json();
  pm.expect(jsonData).to.have.property("username");
  pm.expect(jsonData).to.have.property("password");
  pm.expect(jsonData).to.have.property("accessToken");
});

pm.collectionVariables.set("token", pm.response.json().accessToken);

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This repository is licensed under the MIT License.

## Disclaimer

Please note that the RevueCrafters app/API tested in this project is the property of SoftUni, and this repository only contains my personal testing and automation scripts related to it.


