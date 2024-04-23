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

## Poslední získáné meteorologické data z databáze z dnešního dne

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

## Získáné meteorologické data z databáze pro vybraný den 

`{{baseUrl}}/api/data/meteostation/today/<date>`

## Popis

Tento endpoint GET slouží k získání všech meteorologických dat z databáze pro den <date>. Je požadován JWT token.

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

## Poslední získáné maximální meteorologické data z databáze za dnešní den 

`{{baseUrl}}/api/data/meteostation/today/max`

## Popis

Tento endpoint GET slouží k získání všech maximálních meteorologických dat z databáze za dnešní den. Je požadován JWT token.

## Response Body 200
```json
{
    "battery_bat": "0.00",
    "battery_wh65": "0.00",
    "id": 35683,
    "indoor_humidity_percent": "48.00",
    "indoor_temperature_F": "69.62",
    "outdoor_humidity_percent": "88.00",
    "outdoor_temperature_F": "51.26",
    "pressure_absolute_inHg": "29.23",
    "pressure_relative_inHg": "29.23",
    "rain_event_in": "0.80",
    "rain_hourly_in": "0.00",
    "rain_rate_inhr": "0.00",
    "rain_total_in": "5.68",
    "rain_weekly_in": "0.13",
    "rain_yearly_in": "5.68",
    "solar_radiation_Wm2": "462.43",
    "solar_uv": "4.00",
    "temp_ch1_F": "69.62",
    "temp_humidity_percent": "52.00",
    "time": "Tue, 23 Apr 2024 20:16:46 GMT",
    "wind_angle": "187.00",
    "wind_gust_max_mph": "20.13",
    "wind_gust_mph": "17.45",
    "wind_speed_mph": "11.63"
}
```

## Response Body 401
```json
{
    "msg": "Missing Authorization Header"
}
```

## Poslední získáné minimální meteorologické data z databáze za dnešní den 

`{{baseUrl}}/api/data/meteostation/today/min`

## Popis

Tento endpoint GET slouží k získání všech minimálních meteorologických dat z databáze za dnešní den. Je požadován JWT token.

## Response Body 200
```json
{
    "battery_bat": "0.00",
    "battery_wh65": "0.00",
    "id": 35617,
    "indoor_humidity_percent": "43.00",
    "indoor_temperature_F": "61.88",
    "outdoor_humidity_percent": "58.00",
    "outdoor_temperature_F": "29.12",
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
    "temp_ch1_F": "64.40",
    "temp_humidity_percent": "49.00",
    "time": "Tue, 23 Apr 2024 00:04:41 GMT",
    "wind_angle": "36.00",
    "wind_gust_max_mph": "0.00",
    "wind_gust_mph": "0.00",
    "wind_speed_mph": "0.00"
}
```

## Response Body 401
```json
{
    "msg": "Missing Authorization Header"
}
```

##  Minimální meteorologické data z databáze za vybraný den 

`{{baseUrl}}/api/data/meteostation/min/<date>`

## Popis

Tento endpoint GET slouží k získání minimálních meteorologických dat z databáze za vybraný den. Je požadován JWT token.

## Response Body 200
```json
{
    "battery_bat": "0.00",
    "battery_wh65": "0.00",
    "id": 32889,
    "indoor_humidity_percent": "48.00",
    "indoor_temperature_F": "65.30",
    "outdoor_humidity_percent": "53.00",
    "outdoor_temperature_F": "45.68",
    "pressure_absolute_inHg": "28.93",
    "pressure_relative_inHg": "28.93",
    "rain_event_in": "0.00",
    "rain_hourly_in": "0.00",
    "rain_rate_inhr": "0.00",
    "rain_total_in": "4.42",
    "rain_weekly_in": "1.23",
    "rain_yearly_in": "4.42",
    "solar_radiation_Wm2": "0.00",
    "solar_uv": "0.00",
    "temp_ch1_F": "65.84",
    "temp_humidity_percent": "53.00",
    "time": "Thu, 04 Apr 2024 00:06:14 GMT",
    "wind_angle": "0.00",
    "wind_gust_max_mph": "0.00",
    "wind_gust_mph": "0.00",
    "wind_speed_mph": "0.00"
}
```

## Response Body 401
```json
{
    "msg": "Missing Authorization Header"
}
```

##  Maximální meteorologické data z databáze za vybraný den 

`{{baseUrl}}/api/data/meteostation/max/<date>`

## Popis

Tento endpoint GET slouží k získání maximálních meteorologických dat z databáze za vybraný den. Je požadován JWT token.

## Response Body 200
```json
{
    "battery_bat": "0.00",
    "battery_wh65": "0.00",
    "id": 33032,
    "indoor_humidity_percent": "58.00",
    "indoor_temperature_F": "71.60",
    "outdoor_humidity_percent": "95.00",
    "outdoor_temperature_F": "66.20",
    "pressure_absolute_inHg": "29.00",
    "pressure_relative_inHg": "29.00",
    "rain_event_in": "0.09",
    "rain_hourly_in": "0.09",
    "rain_rate_inhr": "0.28",
    "rain_total_in": "4.54",
    "rain_weekly_in": "1.35",
    "rain_yearly_in": "4.54",
    "solar_radiation_Wm2": "481.03",
    "solar_uv": "4.00",
    "temp_ch1_F": "71.42",
    "temp_humidity_percent": "59.00",
    "time": "Thu, 04 Apr 2024 23:58:42 GMT",
    "wind_angle": "356.00",
    "wind_gust_max_mph": "27.51",
    "wind_gust_mph": "27.51",
    "wind_speed_mph": "14.09"
}
```

## Response Body 401
```json
{
    "msg": "Missing Authorization Header"
}
```


##  Získání všech meteorologický data z databáze za vybraný týden 

`{{baseUrl}}/api/data/weekly_test/<date>`

## Popis

Tento endpoint GET slouží k získání meteorologických dat z databáze za vybraný týden, které jsou v hodinovém intervalu každého dne ve vybraném týdnu. Je požadován JWT token.

## Response Body 200
```json
[
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 305,
        "indoor_humidity_percent": "48.89",
        "indoor_temperature_F": "71.01",
        "outdoor_humidity_percent": "56.51",
        "outdoor_temperature_F": "64.44",
        "pressure_absolute_inHg": "28.56",
        "pressure_relative_inHg": "28.56",
        "rain_event_in": "0.00",
        "rain_hourly_in": "0.00",
        "rain_rate_inhr": "0.00",
        "rain_total_in": "3.19",
        "rain_weekly_in": "0.00",
        "rain_yearly_in": "3.19",
        "solar_radiation_Wm2": "86.85",
        "solar_uv": "0.59",
        "temp_ch1_F": "72.17",
        "temp_humidity_percent": "51.57",
        "week_start": "Mon, 01 Apr 2024 00:00:00 GMT",
        "wind_angle": "248.57",
        "wind_gust_max_mph": "29.11",
        "wind_gust_mph": "13.47",
        "wind_speed_mph": "5.47"
    },
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 306,
        "indoor_humidity_percent": "49.96",
        "indoor_temperature_F": "69.04",
        "outdoor_humidity_percent": "77.47",
        "outdoor_temperature_F": "50.09",
        "pressure_absolute_inHg": "28.73",
        "pressure_relative_inHg": "28.73",
        "rain_event_in": "1.03",
        "rain_hourly_in": "0.05",
        "rain_rate_inhr": "0.05",
        "rain_total_in": "4.22",
        "rain_weekly_in": "1.03",
        "rain_yearly_in": "4.22",
        "solar_radiation_Wm2": "54.90",
        "solar_uv": "0.33",
        "temp_ch1_F": "70.02",
        "temp_humidity_percent": "53.10",
        "week_start": "Tue, 02 Apr 2024 00:00:00 GMT",
        "wind_angle": "274.41",
        "wind_gust_max_mph": "24.94",
        "wind_gust_mph": "9.61",
        "wind_speed_mph": "4.25"
    },
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 307,
        "indoor_humidity_percent": "47.94",
        "indoor_temperature_F": "67.35",
        "outdoor_humidity_percent": "71.39",
        "outdoor_temperature_F": "51.46",
        "pressure_absolute_inHg": "28.88",
        "pressure_relative_inHg": "28.88",
        "rain_event_in": "0.42",
        "rain_hourly_in": "0.00",
        "rain_rate_inhr": "0.00",
        "rain_total_in": "4.38",
        "rain_weekly_in": "1.19",
        "rain_yearly_in": "4.38",
        "solar_radiation_Wm2": "72.74",
        "solar_uv": "0.46",
        "temp_ch1_F": "67.99",
        "temp_humidity_percent": "51.35",
        "week_start": "Wed, 03 Apr 2024 00:00:00 GMT",
        "wind_angle": "260.65",
        "wind_gust_max_mph": "26.84",
        "wind_gust_mph": "10.19",
        "wind_speed_mph": "4.00"
    },
    ...
]
```

## Response Body 401
```json
{
    "msg": "Missing Authorization Header"
}
```

##  Získání všech meteorologický data z databáze za vybraný měsíc 

`{{baseUrl}}/api/data/monthly_test/<date>`

## Popis

Tento endpoint GET slouží k získání meteorologických dat z databáze za vybraný měsíc, které jsou v denním průměru každého dne ve vybraném měsíci. Je požadován JWT token.

## Response Body 200
```json
[
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 305,
        "indoor_humidity_percent": "48.89",
        "indoor_temperature_F": "71.01",
        "outdoor_humidity_percent": "56.51",
        "outdoor_temperature_F": "64.44",
        "pressure_absolute_inHg": "28.56",
        "pressure_relative_inHg": "28.56",
        "rain_event_in": "0.00",
        "rain_hourly_in": "0.00",
        "rain_rate_inhr": "0.00",
        "rain_total_in": "3.19",
        "rain_weekly_in": "0.00",
        "rain_yearly_in": "3.19",
        "solar_radiation_Wm2": "86.85",
        "solar_uv": "0.59",
        "temp_ch1_F": "72.17",
        "temp_humidity_percent": "51.57",
        "week_start": "Mon, 01 Apr 2024 00:00:00 GMT",
        "wind_angle": "248.57",
        "wind_gust_max_mph": "29.11",
        "wind_gust_mph": "13.47",
        "wind_speed_mph": "5.47"
    },
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 306,
        "indoor_humidity_percent": "49.96",
        "indoor_temperature_F": "69.04",
        "outdoor_humidity_percent": "77.47",
        "outdoor_temperature_F": "50.09",
        "pressure_absolute_inHg": "28.73",
        "pressure_relative_inHg": "28.73",
        "rain_event_in": "1.03",
        "rain_hourly_in": "0.05",
        "rain_rate_inhr": "0.05",
        "rain_total_in": "4.22",
        "rain_weekly_in": "1.03",
        "rain_yearly_in": "4.22",
        "solar_radiation_Wm2": "54.90",
        "solar_uv": "0.33",
        "temp_ch1_F": "70.02",
        "temp_humidity_percent": "53.10",
        "week_start": "Tue, 02 Apr 2024 00:00:00 GMT",
        "wind_angle": "274.41",
        "wind_gust_max_mph": "24.94",
        "wind_gust_mph": "9.61",
        "wind_speed_mph": "4.25"
    },
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 307,
        "indoor_humidity_percent": "47.94",
        "indoor_temperature_F": "67.35",
        "outdoor_humidity_percent": "71.39",
        "outdoor_temperature_F": "51.46",
        "pressure_absolute_inHg": "28.88",
        "pressure_relative_inHg": "28.88",
        "rain_event_in": "0.42",
        "rain_hourly_in": "0.00",
        "rain_rate_inhr": "0.00",
        "rain_total_in": "4.38",
        "rain_weekly_in": "1.19",
        "rain_yearly_in": "4.38",
        "solar_radiation_Wm2": "72.74",
        "solar_uv": "0.46",
        "temp_ch1_F": "67.99",
        "temp_humidity_percent": "51.35",
        "week_start": "Wed, 03 Apr 2024 00:00:00 GMT",
        "wind_angle": "260.65",
        "wind_gust_max_mph": "26.84",
        "wind_gust_mph": "10.19",
        "wind_speed_mph": "4.00"
    },
    ...
]
```

## Response Body 401
```json
{
    "msg": "Missing Authorization Header"
}
```



# Získávání agregovaných meteorologických dat

##  Získání všech hodinových agregovaných meteorologický data z databáze 

`{{baseUrl}}/api/data/aggregated`

## Popis

Tento endpoint GET slouží k získání všech hodinových agregovaných meteorologických dat z databáze. Je požadován JWT token.

## Response Body 200
```json
[
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 1,
        "indoor_humidity_percent": "59.60",
        "indoor_temperature_F": "76.39",
        "outdoor_humidity_percent": "84.00",
        "outdoor_temperature_F": "64.83",
        "pressure_absolute_inHg": "28.70",
        "pressure_relative_inHg": "28.70",
        "rain_event_in": "1.40",
        "rain_hourly_in": "0.05",
        "rain_rate_inhr": "0.04",
        "rain_total_in": "13.17",
        "rain_weekly_in": "1.40",
        "rain_yearly_in": "13.17",
        "solar_radiation_Wm2": "118.08",
        "solar_uv": "1.00",
        "temp_ch1_F": "78.04",
        "temp_humidity_percent": "56.00",
        "time": "Tue, 25 Jul 2023 13:00:00 GMT",
        "wind_angle": "234.00",
        "wind_gust_max_mph": "9.39",
        "wind_gust_mph": "7.38",
        "wind_speed_mph": "2.95"
    },
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 2,
        "indoor_humidity_percent": "60.50",
        "indoor_temperature_F": "76.22",
        "outdoor_humidity_percent": "84.17",
        "outdoor_temperature_F": "64.82",
        "pressure_absolute_inHg": "28.69",
        "pressure_relative_inHg": "28.69",
        "rain_event_in": "1.42",
        "rain_hourly_in": "0.03",
        "rain_rate_inhr": "0.01",
        "rain_total_in": "13.19",
        "rain_weekly_in": "1.42",
        "rain_yearly_in": "13.19",
        "solar_radiation_Wm2": "121.19",
        "solar_uv": "0.83",
        "temp_ch1_F": "77.57",
        "temp_humidity_percent": "56.67",
        "time": "Tue, 25 Jul 2023 14:00:00 GMT",
        "wind_angle": "262.17",
        "wind_gust_max_mph": "11.41",
        "wind_gust_mph": "2.99",
        "wind_speed_mph": "1.60"
    },
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 3,
        "indoor_humidity_percent": "59.83",
        "indoor_temperature_F": "75.77",
        "outdoor_humidity_percent": "78.67",
        "outdoor_temperature_F": "65.84",
        "pressure_absolute_inHg": "28.68",
        "pressure_relative_inHg": "28.68",
        "rain_event_in": "1.42",
        "rain_hourly_in": "0.00",
        "rain_rate_inhr": "0.00",
        "rain_total_in": "13.19",
        "rain_weekly_in": "1.42",
        "rain_yearly_in": "13.19",
        "solar_radiation_Wm2": "133.80",
        "solar_uv": "0.83",
        "temp_ch1_F": "77.24",
        "temp_humidity_percent": "56.83",
        "time": "Tue, 25 Jul 2023 15:00:00 GMT",
        "wind_angle": "249.17",
        "wind_gust_max_mph": "11.41",
        "wind_gust_mph": "3.02",
        "wind_speed_mph": "0.86"
    },
    ...
]
```

## Response Body 401
```json
{
    "msg": "Missing Authorization Header"
}
```

##  Získání hodinových agregovaných meteorologický data z databáze za vybraný den 

`{{baseUrl}}/api/data/aggregated/<date>`

## Popis

Tento endpoint GET slouží k získání hodinových agregovaných meteorologických dat z databáze za vybraný den. Je požadován JWT token.

## Response Body 200
```json
[
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 9625,
        "indoor_humidity_percent": "57.67",
        "indoor_temperature_F": "67.79",
        "outdoor_humidity_percent": "92.83",
        "outdoor_temperature_F": "48.83",
        "pressure_absolute_inHg": "28.95",
        "pressure_relative_inHg": "28.95",
        "rain_event_in": "0.05",
        "rain_hourly_in": "0.00",
        "rain_rate_inhr": "0.00",
        "rain_total_in": "4.42",
        "rain_weekly_in": "1.23",
        "rain_yearly_in": "4.42",
        "solar_radiation_Wm2": "0.00",
        "solar_uv": "0.00",
        "temp_ch1_F": "69.41",
        "temp_humidity_percent": "58.00",
        "time": "Thu, 04 Apr 2024 00:00:00 GMT",
        "wind_angle": "258.50",
        "wind_gust_max_mph": "0.82",
        "wind_gust_mph": "0.00",
        "wind_speed_mph": "0.00"
    },
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 9626,
        "indoor_humidity_percent": "57.83",
        "indoor_temperature_F": "67.28",
        "outdoor_humidity_percent": "93.67",
        "outdoor_temperature_F": "48.29",
        "pressure_absolute_inHg": "28.94",
        "pressure_relative_inHg": "28.94",
        "rain_event_in": "0.05",
        "rain_hourly_in": "0.00",
        "rain_rate_inhr": "0.00",
        "rain_total_in": "4.42",
        "rain_weekly_in": "1.23",
        "rain_yearly_in": "4.42",
        "solar_radiation_Wm2": "0.00",
        "solar_uv": "0.00",
        "temp_ch1_F": "68.87",
        "temp_humidity_percent": "58.00",
        "time": "Thu, 04 Apr 2024 01:00:00 GMT",
        "wind_angle": "257.33",
        "wind_gust_max_mph": "2.46",
        "wind_gust_mph": "0.00",
        "wind_speed_mph": "0.00"
    },
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 9627,
        "indoor_humidity_percent": "57.00",
        "indoor_temperature_F": "66.89",
        "outdoor_humidity_percent": "94.00",
        "outdoor_temperature_F": "47.27",
        "pressure_absolute_inHg": "28.93",
        "pressure_relative_inHg": "28.93",
        "rain_event_in": "0.05",
        "rain_hourly_in": "0.00",
        "rain_rate_inhr": "0.00",
        "rain_total_in": "4.42",
        "rain_weekly_in": "1.23",
        "rain_yearly_in": "4.42",
        "solar_radiation_Wm2": "0.00",
        "solar_uv": "0.00",
        "temp_ch1_F": "68.57",
        "temp_humidity_percent": "58.00",
        "time": "Thu, 04 Apr 2024 02:00:00 GMT",
        "wind_angle": "262.00",
        "wind_gust_max_mph": "4.92",
        "wind_gust_mph": "0.82",
        "wind_speed_mph": "0.11"
    },
    ...
]
```

## Response Body 401
```json
{
    "msg": "Missing Authorization Header"
}
```

##  Získání agregovaných meteorologický data z databáze za vybraný den 

`{{baseUrl}}/api/data/daily/<date>`

## Popis

Tento endpoint GET slouží k získání agregovaných meteorologických dat z databáze za vybraný den. Je požadován JWT token.

## Response Body 200
```json
[
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 308,
        "indoor_humidity_percent": "53.99",
        "indoor_temperature_F": "67.98",
        "outdoor_humidity_percent": "78.86",
        "outdoor_temperature_F": "53.59",
        "pressure_absolute_inHg": "28.96",
        "pressure_relative_inHg": "28.96",
        "rain_event_in": "0.05",
        "rain_hourly_in": "0.00",
        "rain_rate_inhr": "0.00",
        "rain_total_in": "4.43",
        "rain_weekly_in": "1.24",
        "rain_yearly_in": "4.43",
        "solar_radiation_Wm2": "86.46",
        "solar_uv": "0.62",
        "temp_ch1_F": "68.25",
        "temp_humidity_percent": "56.99",
        "week_start": "Thu, 04 Apr 2024 00:00:00 GMT",
        "wind_angle": "261.38",
        "wind_gust_max_mph": "19.99",
        "wind_gust_mph": "7.85",
        "wind_speed_mph": "3.05"
    }
]
```

## Response Body 401
```json
{
    "msg": "Missing Authorization Header"
}
```

##  Získání všech agregovaných meteorologický data z databáze

`{{baseUrl}}/api/data/daily`

## Popis

Tento endpoint GET slouží k získání všech agregovaných meteorologických dat z databáze. Je požadován JWT token.

## Response Body 200
```json
[
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 1,
        "indoor_humidity_percent": "59.66",
        "indoor_temperature_F": "76.14",
        "outdoor_humidity_percent": "85.41",
        "outdoor_temperature_F": "63.85",
        "pressure_absolute_inHg": "28.69",
        "pressure_relative_inHg": "28.69",
        "rain_event_in": "1.48",
        "rain_hourly_in": "0.03",
        "rain_rate_inhr": "0.02",
        "rain_total_in": "13.25",
        "rain_weekly_in": "1.48",
        "rain_yearly_in": "13.25",
        "solar_radiation_Wm2": "72.81",
        "solar_uv": "0.45",
        "temp_ch1_F": "78.04",
        "temp_humidity_percent": "55.59",
        "week_start": "Tue, 25 Jul 2023 00:00:00 GMT",
        "wind_angle": "175.23",
        "wind_gust_max_mph": "11.23",
        "wind_gust_mph": "2.23",
        "wind_speed_mph": "0.87"
    },
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 2,
        "indoor_humidity_percent": "54.71",
        "indoor_temperature_F": "75.01",
        "outdoor_humidity_percent": "87.49",
        "outdoor_temperature_F": "57.55",
        "pressure_absolute_inHg": "28.83",
        "pressure_relative_inHg": "28.83",
        "rain_event_in": "1.78",
        "rain_hourly_in": "0.01",
        "rain_rate_inhr": "0.01",
        "rain_total_in": "13.55",
        "rain_weekly_in": "1.78",
        "rain_yearly_in": "13.55",
        "solar_radiation_Wm2": "75.57",
        "solar_uv": "0.45",
        "temp_ch1_F": "76.38",
        "temp_humidity_percent": "52.37",
        "week_start": "Wed, 26 Jul 2023 00:00:00 GMT",
        "wind_angle": "201.86",
        "wind_gust_max_mph": "9.05",
        "wind_gust_mph": "2.79",
        "wind_speed_mph": "1.03"
    },
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 3,
        "indoor_humidity_percent": "48.73",
        "indoor_temperature_F": "71.67",
        "outdoor_humidity_percent": "68.27",
        "outdoor_temperature_F": "61.80",
        "pressure_absolute_inHg": "28.96",
        "pressure_relative_inHg": "28.96",
        "rain_event_in": "1.05",
        "rain_hourly_in": "0.00",
        "rain_rate_inhr": "0.00",
        "rain_total_in": "13.71",
        "rain_weekly_in": "1.94",
        "rain_yearly_in": "13.71",
        "solar_radiation_Wm2": "143.02",
        "solar_uv": "1.07",
        "temp_ch1_F": "72.85",
        "temp_humidity_percent": "46.81",
        "week_start": "Thu, 27 Jul 2023 00:00:00 GMT",
        "wind_angle": "263.05",
        "wind_gust_max_mph": "8.71",
        "wind_gust_mph": "3.00",
        "wind_speed_mph": "1.12"
    },
    ...
]
```

## Response Body 401
```json
{
    "msg": "Missing Authorization Header"
}
```


##  Získání všech agregovaných meteorologický data z databáze

`{{baseUrl}}/api/data/weekly`

## Popis

Tento endpoint GET slouží k získání všech týdenních agregovaných meteorologických dat z databáze. Je požadován JWT token.

## Response Body 200
```json
[
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 1,
        "indoor_humidity_percent": "59.51",
        "indoor_temperature_F": "73.44",
        "outdoor_humidity_percent": "79.48",
        "outdoor_temperature_F": "63.89",
        "pressure_absolute_inHg": "28.86",
        "pressure_relative_inHg": "28.86",
        "rain_event_in": "0.75",
        "rain_hourly_in": "0.01",
        "rain_rate_inhr": "0.01",
        "rain_total_in": "13.67",
        "rain_weekly_in": "1.55",
        "rain_yearly_in": "13.67",
        "solar_radiation_Wm2": "100.80",
        "solar_uv": "0.70",
        "temp_ch1_F": "74.73",
        "temp_humidity_percent": "56.48",
        "week_start": "Sun, 30 Jul 2023 00:00:00 GMT",
        "wind_angle": "234.42",
        "wind_gust_max_mph": "9.24",
        "wind_gust_mph": "2.86",
        "wind_speed_mph": "1.11"
    },
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 2,
        "indoor_humidity_percent": "60.65",
        "indoor_temperature_F": "73.31",
        "outdoor_humidity_percent": "78.70",
        "outdoor_temperature_F": "64.49",
        "pressure_absolute_inHg": "28.81",
        "pressure_relative_inHg": "28.81",
        "rain_event_in": "0.17",
        "rain_hourly_in": "0.01",
        "rain_rate_inhr": "0.01",
        "rain_total_in": "14.16",
        "rain_weekly_in": "0.21",
        "rain_yearly_in": "14.16",
        "solar_radiation_Wm2": "63.16",
        "solar_uv": "0.36",
        "temp_ch1_F": "73.70",
        "temp_humidity_percent": "59.12",
        "week_start": "Sun, 06 Aug 2023 00:00:00 GMT",
        "wind_angle": "235.59",
        "wind_gust_max_mph": "7.69",
        "wind_gust_mph": "2.91",
        "wind_speed_mph": "1.11"
    },
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 3,
        "indoor_humidity_percent": "59.38",
        "indoor_temperature_F": "69.56",
        "outdoor_humidity_percent": "74.23",
        "outdoor_temperature_F": "62.27",
        "pressure_absolute_inHg": "29.11",
        "pressure_relative_inHg": "29.11",
        "rain_event_in": "0.42",
        "rain_hourly_in": "0.00",
        "rain_rate_inhr": "0.00",
        "rain_total_in": "15.88",
        "rain_weekly_in": "1.33",
        "rain_yearly_in": "15.88",
        "solar_radiation_Wm2": "100.32",
        "solar_uv": "0.72",
        "temp_ch1_F": "70.91",
        "temp_humidity_percent": "56.81",
        "week_start": "Sun, 13 Aug 2023 00:00:00 GMT",
        "wind_angle": "239.28",
        "wind_gust_max_mph": "7.15",
        "wind_gust_mph": "2.55",
        "wind_speed_mph": "0.98"
    },
]
```

## Response Body 401
```json
{
    "msg": "Missing Authorization Header"
}
```

##  Získání všech měsíčních agregovaných meteorologický data z databáze

`{{baseUrl}}/api/data/monthly`

## Popis

Tento endpoint GET slouží k získání všech měsíčních agregovaných meteorologických dat z databáze. Je požadován JWT token.

## Response Body 200
```json
[
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 1,
        "indoor_humidity_percent": "59.51",
        "indoor_temperature_F": "73.44",
        "next_month_start": "Sat, 01 Jul 2023 00:00:00 GMT",
        "outdoor_humidity_percent": "79.48",
        "outdoor_temperature_F": "63.89",
        "pressure_absolute_inHg": "28.86",
        "pressure_relative_inHg": "28.86",
        "rain_event_in": "0.75",
        "rain_hourly_in": "0.01",
        "rain_rate_inhr": "0.01",
        "rain_total_in": "13.67",
        "rain_weekly_in": "1.55",
        "rain_yearly_in": "13.67",
        "solar_radiation_Wm2": "100.80",
        "solar_uv": "0.70",
        "temp_ch1_F": "74.73",
        "temp_humidity_percent": "56.48",
        "wind_angle": "234.42",
        "wind_gust_max_mph": "9.24",
        "wind_gust_mph": "2.86",
        "wind_speed_mph": "1.11"
    },
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 2,
        "indoor_humidity_percent": "60.26",
        "indoor_temperature_F": "74.51",
        "next_month_start": "Tue, 01 Aug 2023 00:00:00 GMT",
        "outdoor_humidity_percent": "74.70",
        "outdoor_temperature_F": "68.23",
        "pressure_absolute_inHg": "29.03",
        "pressure_relative_inHg": "29.03",
        "rain_event_in": "0.17",
        "rain_hourly_in": "0.00",
        "rain_rate_inhr": "0.00",
        "rain_total_in": "15.64",
        "rain_weekly_in": "0.48",
        "rain_yearly_in": "15.64",
        "solar_radiation_Wm2": "91.55",
        "solar_uv": "0.63",
        "temp_ch1_F": "75.50",
        "temp_humidity_percent": "58.32",
        "wind_angle": "206.94",
        "wind_gust_max_mph": "7.16",
        "wind_gust_mph": "2.04",
        "wind_speed_mph": "0.75"
    },
    {
        "battery_bat": "0.00",
        "battery_wh65": "0.00",
        "id": 3,
        "indoor_humidity_percent": "58.38",
        "indoor_temperature_F": "74.19",
        "next_month_start": "Fri, 01 Sep 2023 00:00:00 GMT",
        "outdoor_humidity_percent": "77.88",
        "outdoor_temperature_F": "63.62",
        "pressure_absolute_inHg": "29.09",
        "pressure_relative_inHg": "29.09",
        "rain_event_in": "0.14",
        "rain_hourly_in": "0.00",
        "rain_rate_inhr": "0.00",
        "rain_total_in": "18.20",
        "rain_weekly_in": "0.42",
        "rain_yearly_in": "18.20",
        "solar_radiation_Wm2": "62.77",
        "solar_uv": "0.38",
        "temp_ch1_F": "75.41",
        "temp_humidity_percent": "57.05",
        "wind_angle": "169.25",
        "wind_gust_max_mph": "5.88",
        "wind_gust_mph": "1.64",
        "wind_speed_mph": "0.59"
    },
    ...
]
```

## Response Body 401
```json
{
    "msg": "Missing Authorization Header"
}
```





