# Weather_API_documentation
RESTful API dokumentace k dotazování na lokální server k poskytnutí meteorologických dat z lokální meteorologické stanice.
## Přihlášení 

`{{baseUrl}}/api/login`

## Popis

Tento endpoint slouží k přihlášení uživatele pomocí jména a hesla.

## Request Body

```json
{
    "username": "test",
    "password": "test"
}
```

## Response Body
```json
{
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJmcmVzaCI6ZmFsc2UsImlhdCI6MTcxMzg5MzQwNywianRpIjoiMzFmMTUwNGMtZTE3Ni00OTNkLWExMTgtMTIwMzVmOWY4ZjU5IiwidHlwZSI6ImFjY2VzcyIsInN1YiI6eyJ1c2VybmFtZSI6InRlc3QifSwibmJmIjoxNzEzODkzNDA3LCJleHAiOjE3MTM4OTcwMDd9.WVqH4QvPwA4S6GtCL0Fln0CplcufK6haJEtCSZ6sVtI"
}
```

## Registrace 

`{{baseUrl}}/api/register`

## Popis

Tento endpoint slouží k registraci uživatele pomocí jména a hesla a ID meteorologické stanice.

## Request Body

```json
{
    "username": "test",
    "password": "test",
    "code" : "jei4Rail"
}
```

## Response Body 200
```json
{
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJmcmVzaCI6ZmFsc2UsImlhdCI6MTcxMzg5MzkzMCwianRpIjoiZWM3OWQ1NjgtZjUzNi00OGFhLThhNDUtYTFkODFlNjYyY2NhIiwidHlwZSI6ImFjY2VzcyIsInN1YiI6InRlc3RfdnNiIiwibmJmIjoxNzEzODkzOTMwLCJleHAiOjE3MTM4OTc1MzB9.04fcohvfiwv0oNJjQw6n7zlMy_O0e1YVcttdIXG4qrk",
    "message": "User successfully registered"
}
```
## Response Body 400
```json
{
    "error": "Username already exists"
}
```


