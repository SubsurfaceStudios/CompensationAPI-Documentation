# Compensation API Documentation

# Authentication
`/api/auth/`
# Description

Authentication is one of the most essential parts of the Compensation API, and likely
the one you will use the most.

# Login

## Relative Address
`/api/auth/login`

## Description
Logging in is the prerequisite to almost every important request you can make to the server, 
including WebSockets, managing your account, viewing private rooms, and more.

## Example Request - Single Factor Authentication

This example request will log into the specified account, granting you an authentication token you can use to perform further requests.

<details>  
<summary>Request</summary>  

```
URL:
https://api.compensationvr.tk/api/auth/login

Headers:
Content-Type: application/json
Content-Length: <length>

Body:
```
```json
{
    "username": "<username>",
    "password": "<password>"
}
```

</details>  

The server (should) respond with:  

<details>  
<summary>Response</summary>

```json
{
	"userID": "<user id>",
	"username": "<username>",
	"accessToken": "<token>",
	"developer": <developer*>
}
```

</details>

*The "developer" property is only set to true if you have Developer permissions on the API.
## Example Request - Two Factor Authentication

This example request is used if you have enabled Two Factor Authentication on your account, and involves TOTP codes.  
<strong>Wherever we use `<TOTP>`, insert your TOTP code from your authenticator app.</strong>

<details>
<summary>Request</summary>

```
URL:
https://api.compensationvr.tk/api/auth/login

Headers:
Content-Type: application/json
Content-Length: <length>

Body:
```
```json
{
    "username": "<username>",
    "password: "<password>",
    "code": "<TOTP>"
}
```
</details>

The server (should) respond with:

<details>
<summary>Response</summary>

```json
{
	"userID": "<user id>",
	"username": "<username>",
	"accessToken": "<token>",
	"developer": <developer*>
}
```

</details>

*The "developer" property is only set to true if you have Developer permissions on the API.

# Create Account

## Relative Address
`/api/auth/create`

## Description
This endpoint is used to create a new user account on the API. Please note that abuse of this will result in your computer being blacklisted from the API entirely.  
This includes vulgar/inappropriate usernames, creating too many accounts too quickly, and other offenses at API team discretion.

## Example Request

<details>
<summary>Request</summary>

```
URL:
https://api.compensationvr.tk/api/auth/create

Headers:
Content-Type: application/json
Content-Length: <length>

Body:
```
```json
{
    "username": "<username>",
    "password": "<password>",
    "nickname": "<nickname>*"
}
```

The Nickname field is optional, and will default to your username if not specified.

</details>

The server (should) respond with:

<details>
<summary>Response</summary>

No response is returned by this request.

</details>

# Check Token

## Relative Address
`/api/auth/check`
## Description
Returns HTTP 200 OK if your authentication token is valid.

## Example Request

<details>
<summary>Request</summary>

```
URL:
https://api.compensationvr.tk/api/auth/check

Headers:
Authorization: Bearer <token>

Body: N/A
```

</details>