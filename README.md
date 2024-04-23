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

## Validace 

`{{baseUrl}}/api/is_valid`

## Popis

Tento endpoint slouží k validaci API serveru.

## Response Body 200
```json
{
    "valid_token": 1
}
```

## Sloupace databáze 

`{{baseUrl}}/api/columns`

## Popis

Tento endpoint slouží k získání názvů sloupců databáze. Je požadován JWT token.

## Response Body 200
```json
{
    "rows": [
        "id",
        "time",
        "indoor_temperature_F",
        "indoor_humidity_percent",
        "pressure_relative_inHg",
        "pressure_absolute_inHg",
        "outdoor_temperature_F",
        "outdoor_humidity_percent",
        "wind_angle",
        "wind_speed_mph",
        "wind_gust_mph",
        "wind_gust_max_mph",
        "solar_radiation_Wm2",
        "solar_uv",
        "rain_rate_inhr",
        "rain_event_in",
        "rain_hourly_in",
        "rain_weekly_in",
        "rain_yearly_in",
        "rain_total_in",
        "temp_ch1_F",
        "temp_humidity_percent",
        "battery_wh65",
        "battery_bat"
    ]
}
```

## Response Body 401
```json
{
    "msg": "Missing Authorization Header"
}
```

## Sloupace databáze 

`{{baseUrl}}/api/columns`

## Popis

Tento endpoint slouží k získání názvů sloupců databáze. Je požadován JWT token.

## Response Body 200
```json
{
    "rows": [
        "id",
        "time",
        "indoor_temperature_F",
        "indoor_humidity_percent",
        "pressure_relative_inHg",
        "pressure_absolute_inHg",
        "outdoor_temperature_F",
        "outdoor_humidity_percent",
        "wind_angle",
        "wind_speed_mph",
        "wind_gust_mph",
        "wind_gust_max_mph",
        "solar_radiation_Wm2",
        "solar_uv",
        "rain_rate_inhr",
        "rain_event_in",
        "rain_hourly_in",
        "rain_weekly_in",
        "rain_yearly_in",
        "rain_total_in",
        "temp_ch1_F",
        "temp_humidity_percent",
        "battery_wh65",
        "battery_bat"
    ]
}
```

## Response Body 401
```json
{
    "msg": "Missing Authorization Header"
}
```







