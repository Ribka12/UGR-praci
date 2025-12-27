API Documentation for Evangadi Forum
Authentication Middleware
Endpoint: /api/user/checkUser
Method: GET
Description: Checks the current authenticated user's information.
Request Headers
● Authorization: Bearer token
Successful Response
Status Code: 200 OK
Content-Type: application/json
{
"message": "Valid user",
"username": “Kebede”,
“userid”:”123”
}
Error Responses
Status Code: 401 Unauthorized
Description: Authentication credentials were missing or incorrect.
{
"error": "Unauthorized",
"message": "Authentication invalid"
}
