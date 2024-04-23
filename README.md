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











