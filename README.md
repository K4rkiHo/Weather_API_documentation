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

# Získávání dat z meteorologické stanice

## Poslední získáné meteorologické data z databáze 

`{{baseUrl}}/api/data/last_data`

## Popis

Tento endpoint GET slouží k získání posledních meteorologických dat z databáze. Je požadován JWT token.

## Response Body 200
```json
{
    "battery_bat": "0.00",
    "battery_wh65": "0.00",
    "id": 35682,
    "indoor_humidity_percent": "45.00",
    "indoor_temperature_F": "69.26",
    "outdoor_humidity_percent": "69.00",
    "outdoor_temperature_F": "46.94",
    "pressure_absolute_inHg": "28.93",
    "pressure_relative_inHg": "28.93",
    "rain_event_in": "0.00",
    "rain_hourly_in": "0.00",
    "rain_rate_inhr": "0.00",
    "rain_total_in": "5.68",
    "rain_weekly_in": "0.13",
    "rain_yearly_in": "5.68",
    "solar_radiation_Wm2": "0.00",
    "solar_uv": "0.00",
    "temp_ch1_F": "69.44",
    "temp_humidity_percent": "51.00",
    "time": "Tue, 23 Apr 2024 20:06:45 GMT",
    "wind_angle": "98.00",
    "wind_gust_max_mph": "20.13",
    "wind_gust_mph": "2.46",
    "wind_speed_mph": "2.24"
}
```

## Response Body 401
```json
{
    "msg": "Missing Authorization Header"
}
```

## Poslední získáné meteorologické data z databáze 

`{{baseUrl}}/api/data/meteostation/today`

## Popis

Tento endpoint GET slouží k získání všech meteorologických dat z databáze za dnešní den. Je požadován JWT token.

## Response Body 200
```json
[
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 35617,
        "indoor_humidity_percent": "46.00",
        "indoor_temperature_F": "64.76",
        "outdoor_humidity_percent": "83.00",
        "outdoor_temperature_F": "30.56",
        "pressure_absolute_inHg": "29.23",
        "pressure_relative_inHg": "29.23",
        "rain_event_in": "0.80",
        "rain_hourly_in": "0.00",
        "rain_rate_inhr": "0.00",
        "rain_total_in": "5.68",
        "rain_weekly_in": "0.13",
        "rain_yearly_in": "5.68",
        "solar_radiation_Wm2": "0.00",
        "solar_uv": "0.00",
        "temp_ch1_F": "67.82",
        "temp_humidity_percent": "49.00",
        "time": "Tue, 23 Apr 2024 00:04:41 GMT",
        "wind_angle": "113.00",
        "wind_gust_max_mph": "0.00",
        "wind_gust_mph": "0.00",
        "wind_speed_mph": "0.00"
    },
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 35618,
        "indoor_humidity_percent": "47.00",
        "indoor_temperature_F": "64.94",
        "outdoor_humidity_percent": "85.00",
        "outdoor_temperature_F": "30.02",
        "pressure_absolute_inHg": "29.22",
        "pressure_relative_inHg": "29.22",
        "rain_event_in": "0.80",
        "rain_hourly_in": "0.00",
        "rain_rate_inhr": "0.00",
        "rain_total_in": "5.68",
        "rain_weekly_in": "0.13",
        "rain_yearly_in": "5.68",
        "solar_radiation_Wm2": "0.00",
        "solar_uv": "0.00",
        "temp_ch1_F": "67.82",
        "temp_humidity_percent": "50.00",
        "time": "Tue, 23 Apr 2024 00:14:42 GMT",
        "wind_angle": "113.00",
        "wind_gust_max_mph": "0.00",
        "wind_gust_mph": "0.00",
        "wind_speed_mph": "0.00"
    },
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 35619,
        "indoor_humidity_percent": "48.00",
        "indoor_temperature_F": "64.04",
        "outdoor_humidity_percent": "85.00",
        "outdoor_temperature_F": "29.84",
        "pressure_absolute_inHg": "29.22",
        "pressure_relative_inHg": "29.22",
        "rain_event_in": "0.80",
        "rain_hourly_in": "0.00",
        "rain_rate_inhr": "0.00",
        "rain_total_in": "5.68",
        "rain_weekly_in": "0.13",
        "rain_yearly_in": "5.68",
        "solar_radiation_Wm2": "0.00",
        "solar_uv": "0.00",
        "temp_ch1_F": "67.64",
        "temp_humidity_percent": "49.00",
        "time": "Tue, 23 Apr 2024 00:24:43 GMT",
        "wind_angle": "113.00",
        "wind_gust_max_mph": "0.00",
        "wind_gust_mph": "0.00",
        "wind_speed_mph": "0.00"
    },
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 35620,
        "indoor_humidity_percent": "47.00",
        "indoor_temperature_F": "64.04",
        "outdoor_humidity_percent": "85.00",
        "outdoor_temperature_F": "29.84",
        "pressure_absolute_inHg": "29.22",
        "pressure_relative_inHg": "29.22",
        "rain_event_in": "0.80",
        "rain_hourly_in": "0.00",
        "rain_rate_inhr": "0.00",
        "rain_total_in": "5.68",
        "rain_weekly_in": "0.13",
        "rain_yearly_in": "5.68",
        "solar_radiation_Wm2": "0.00",
        "solar_uv": "0.00",
        "temp_ch1_F": "67.28",
        "temp_humidity_percent": "49.00",
        "time": "Tue, 23 Apr 2024 00:34:44 GMT",
        "wind_angle": "113.00",
        "wind_gust_max_mph": "0.00",
        "wind_gust_mph": "0.00",
        "wind_speed_mph": "0.00"
    }
    ...
]
```

## Response Body 401
```json
{
    "msg": "Missing Authorization Header"
}
```









