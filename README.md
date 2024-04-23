# Weather_API_documentation
RESTful API dokumentace k dotazování na lokální server k poskytnutí meteorologických dat z lokální meteorologické stanice.
## URL

`{{baseUrl}}/api/login`

## Popis

Tento endpoint slouží k přihlášení uživatele pomocí jména a hesla.

## Request Body

```json
{
    "username": "test",
    "password": "test"
}

## Response Body
```json
{
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJmcmVzaCI6ZmFsc2UsImlhdCI6MTcxMzg5MzQwNywianRpIjoiMzFmMTUwNGMtZTE3Ni00OTNkLWExMTgtMTIwMzVmOWY4ZjU5IiwidHlwZSI6ImFjY2VzcyIsInN1YiI6eyJ1c2VybmFtZSI6InRlc3QifSwibmJmIjoxNzEzODkzNDA3LCJleHAiOjE3MTM4OTcwMDd9.WVqH4QvPwA4S6GtCL0Fln0CplcufK6haJEtCSZ6sVtI"
}
