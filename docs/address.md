# User API Spec

## Register User

Endpoint : POST /api/users

Request Body :

```json
{
  "username": "alpharajasa",
  "password": "atmint",
  "name": "Kang Cilok"
}
```

Response Body (Success) :

```json
{
  "data": "OK"
}
```

Response Body (Failed) :

```json
{
  "errors": "Username must not blank, ???"
}
```

## Login User

Endpoint : POST /api/auth/login

Request Body :

```json
{
  "username": "alpharajasa",
  "password": "atmint"
}
```

Response Body (Success) :

```json
{
  "data": {
    "token": "TOKEN",
    "expiredAt": 3128127128973 // milliseconds
  }
}
```

Response Body (Failed, 401) :

```json
{
  "errors": "Username or password wrong"
}
```

## Get User

Endpoint : GET /api/users/current

Request Header :

- X-API-TOKEN : Token (Mandatory)

Response Body (Success) :

```json
{
  "data": {
    "username": "alpharajasa",
    "name": "Kang Cilok"
  }
}
```

Response Body (Failed, 401) :

```json
{
  "errors": "Unauthorized"
}
```

## Update User

Endpoint : PATCH /api/users/current

Request Header :

- X-API-TOKEN : Token (Mandatory)

Request Body :

```json
{
  "name": "Kang Cilok", // put if only want to update name
  "password": "New PW" // put if only want to update password
}
```

Response Body (Success) :

```json
{
  "data": {
    "username": "alpharajasa",
    "name": "Kang Cilok"
  }
}
```

Response Body (Failed, 401) :

```json
{
  "errors": "Unauthorized"
}
```

## Logout User

Endpoint : DELETE /api/auth/logout

Request Header :

- X-API-TOKEN : Token (Mandatory)

Response Body (Success) :

```json
{
  "data": "OK"
}
```
