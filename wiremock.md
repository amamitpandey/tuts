# WireMock
some examples:
https://wiremock.org/docs/stubbing/

https://github.com/codefarm0/WireMock/tree/master/ticketbookingservice

## to generate a static response for testing, outside the application.
Steps
1. Download wiremock.jar file and move to a specific folder
2. open treminal and run the jar file: $ java -jar /path/wirwmock.jar
3. now server is running on localhost:8080 and --files and mapping dir have been created.
4. to save in local with json file use post method: localhost:8080/--admin/mappings/save // try first than save, try with below json in body
`
{
  "request": {
    "method": "GET",
    "url": "/randomApiName"
  },

  "response": {
    "status": 200,
    "body": "Hello, world!",
    "headers": {
        "Content-Type": "application/json"
    }
  }
}

`
5. test default api from postman or browser: localhost:8080/randomApiName
6. test on diffrent $ java -jar /path/wirwmock.jar -port=8081
7. using queryParamtertes .* we can accept any argument
8. use "jsonBody" for save json data
