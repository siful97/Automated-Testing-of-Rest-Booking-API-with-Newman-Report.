### **Rest Booking API Testing with Postman Newman**
This project demonstrates API testing using Postman, providing a collection of tests to validate various endpoints of the API. 

### **Features**

- Tests for GET, POST, PUT, DELETE requests
- Collection of tests covering different API endpoints
- Environment setup for easy switching between environments
- Pre-request scripts for data setup
- Test scripts for assertions and validations

## API Documentation:
- https://shorturl.at/xtAnA
  
### **Technology used:**
- Postman
- Newman

### **Prerequisite:**
- Node Js
- Newman
- Newman Html Report Library

### **Installation**

1. Postman: If you haven't already, [download and install Postman.](https://www.postman.com/downloads/)
2. Clone the repository:
 ```console 
  git clone https://github.com/siful97/Automated-Testing-of-Rest-Booking-API-with-Newman-Report..git

```
3. Import the Postman collection:
    - Open Postman.
    - Click on the Import button.
    - Select the file from the repository.
4. Import the Postman environment:
    - In Postman, click on the gear icon in the top right corner.
    - Select **Import** and choose the file.
5. Newman and Report Installation Process:
    - Newman Install Command:
     ```console 
      npm install -g newman
    ```
    - Newman Html Report Install Command:
     ```console 
      npm install -g newman-reporter-htmlextra
    ```
### **Usage**
1. Select Environment:
    -   In Postman, select the appropriate environment (e.g., Development, Production) from the top-right dropdown.
3. Run Collection:
    -   Select the imported collection from the Collections sidebar.
    -   Click on the Runner button to open the collection runner.
    -   Select the desired environment.
    -   Click Start Test to run the collection.
8. View Results:
    -   Once the tests are complete, view the results in the Runner tab.
    -   Detailed test results can be viewed for each request.

## **Testing**

## Test Case Scenarios:

## _**1. Create New Booking**_

### Request URL: https://restful-booker.herokuapp.com/booking/
### Request Method: POST
### Pre-request Script:
```console 
    var firstName = pm.variables.replaceIn("{{$randomFirstName}}")
    pm.environment.set("firstName", firstName)
    console.log("First Name Value "+firstName)
    
    var lastName = pm.variables.replaceIn("{{$randomLastName}}")
    pm.environment.set("lastName", lastName)
    console.log("Last Name Value "+lastName)
    
    var totalPrice = pm.variables.replaceIn("{{$randomInt}}")
    pm.environment.set("totalPrice", totalPrice)
    console.log(totalPrice)
    
    var depositPaid = pm.variables.replaceIn("{{$randomBoolean}}")
    pm.environment.set("depositPaid", depositPaid)
    console.log(depositPaid)
    
    //Date
    const moment = require('moment')
    const today = moment()
    pm.environment.set("checkin", today.add(1,'d').format("YYYY-MM-DD"))
    pm.environment.set("checkout",today.add(5,'d').format("YYYY-MM-DD") )
    
    var additionalNeeds = pm.variables.replaceIn("{{$randomNoun}}")
    pm.environment.set("additionalNeeds", additionalNeeds)
```
  **Request Body:** 
 ```console 
  {
	  "firstname" : "{{firstName}}",
	  "lastname" : "{{lastName}}",
	  "totalprice" : {{totalPrice}},
	  "depositpaid" : {{depositPaid}},
	  "bookingdates" : {
    	  "checkin" : "{{checkin}}",
    	  "checkout" : "{{checkout}}"
	  },
	  "additionalneeds" : "{{additionalNeeds}}"
  }
```
  **Response Body:**
 ```console 
  {
      "bookingid": 4334,
      "booking": {
          "firstname": "Joelle",
          "lastname": "Krajcik",
          "totalprice": 266,
          "depositpaid": true,
          "bookingdates": {
              "checkin": "2024-03-15",
              "checkout": "2024-03-20"
          },
          "additionalneeds": "monitor"
      }
  }
```
 ## _**2. Get Booking Details By ID**_
### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: GET
### Response Body:
 ```console 
{
    "firstname": "D'angelo",
    "lastname": "Feeney",
    "totalprice": 757,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2024-03-15",
        "checkout": "2024-03-20"
    },
    "additionalneeds": "hard drive"
}
```
## _**3. Create A Token For Authentication.**_
### Request URL: https://restful-booker.herokuapp.com/auth
### Request Method: POST
### Pre-request Script: None
### Request Body:
 ```console 
{
	"username": "admin",
	"password": "password123"
}
```
  **Response Body:**
 ```console 
{
    "token": "06eb798bf6f2caa"
}
```

 ## _**4. Update the Booking Details**_
### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: PUT
### Pre-request Script:
```console 
    var firstName = pm.variables.replaceIn("{{$randomFirstName}}")
    pm.environment.set("firstName", firstName)
    console.log("First Name Value "+firstName)
    
    var lastName = pm.variables.replaceIn("{{$randomLastName}}")
    pm.environment.set("lastName", lastName)
    console.log("Last Name Value "+lastName)
    
    var totalPrice = pm.variables.replaceIn("{{$randomInt}}")
    pm.environment.set("totalPrice", totalPrice)
    console.log(totalPrice)
    
    var depositPaid = pm.variables.replaceIn("{{$randomBoolean}}")
    pm.environment.set("depositPaid", depositPaid)
    console.log(depositPaid)
    
    //Date
    const moment = require('moment')
    const today = moment()
    pm.environment.set("checkin", today.add(1,'d').format("YYYY-MM-DD"))
    pm.environment.set("checkout",today.add(5,'d').format("YYYY-MM-DD") )
    
    var additionalNeeds = pm.variables.replaceIn("{{$randomNoun}}")
    pm.environment.set("additionalNeeds", additionalNeeds)
```
  **Request Body:** 
 ```console 
  {
	  "firstname" : "{{firstName}}",
	  "lastname" : "{{lastName}}",
	  "totalprice" : {{totalPrice}},
	  "depositpaid" : {{depositPaid}},
	  "bookingdates" : {
    	  "checkin" : "{{checkin}}",
    	  "checkout" : "{{checkout}}"
	  },
	  "additionalneeds" : "{{additionalNeeds}}"
  }
```
  **Response Body:**
 ```console 
  {
      "bookingid": 4334,
      "booking": {
          "firstname": "Joelle",
          "lastname": "Krajcik",
          "totalprice": 266,
          "depositpaid": true,
          "bookingdates": {
              "checkin": "2024-03-15",
              "checkout": "2024-03-20"
          },
          "additionalneeds": "monitor"
      }
  }
```

 ## _**5. Delete Booking Record**_

### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
### Request Method: DELETE
### Response Body: None 

## Run Command:  
- Run Command for Console: 
```console 
newman run Booking.postman_collection.json -e Booking.postman_environment.json  
```
- Run Command for Report: 
```console 
newman run Booking.postman_collection.json -e Booking.postman_environment.json -r cli,htmlextra
```

## Newman Report Summary:
![Newman Report Summary](https://github.com/user-attachments/assets/be556148-cfd2-4351-a5f5-4943ec3b4df1)
![Newman Report Summary](https://github.com/user-attachments/assets/bf3bf1ef-4e41-47f5-8114-59183701fe8e)
![Newman Report Summary](https://github.com/user-attachments/assets/a79167b6-c274-4582-96a8-ec5edc7f7269)
![Newman Report Summary](https://github.com/user-attachments/assets/fa2156de-aa9e-47d3-b126-5bb108ca6126)



