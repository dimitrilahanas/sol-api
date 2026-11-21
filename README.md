# Sol. API

A FastAPI service that fetches, processes and serves Mars weather data from NASA's InSight lander. It's the backend for [**sol-app**](https://github.com/dimitrilahanas/sol-app).

---

## About

NASA's InSight API returns deeply nested JSON that isn't friendly for an app to consume directly. Sol. API handles the fetching, parsing and modelling, and exposes clean, flat endpoints instead.

```
NASA InSight API  →  sol-api (FastAPI)  →  sol-app (Flutter)
```

Built to practise:

- Working with REST APIs and environment variables
- Parsing nested JSON
- Structuring reusable classes and models
- Serving data through a simple API

---

## Features

- List every available sol
- Get the most recent sol
- Get detailed weather for any sol:
  - Average temperature
  - Martian season
  - Most common wind direction
  - Average wind speed

---

## Tech Stack

- **Python 3.9+**
- **FastAPI**: web API framework
- **Requests**: calls to the NASA API
- **python-dotenv**: loads the NASA API key from `.env`

---

## Endpoints

| Endpoint | Description |
|---|---|
| `GET /available` | List of all available sols |
| `GET /{sol}` | Weather data for the given sol |

Example `GET /1001`:

```json
{
  "temperature": -65.2,
  "season": "spring",
  "wind_direction": "NW",
  "wind_speed": 5.6
}
```

Interactive docs are available at `/docs` while the server is running.

---

## Project Structure

```
sol-api/
├── main.py             # FastAPI app and endpoints
├── .env                # NASA API key (not committed)
└── app/
    ├── __init__.py
    ├── mars_data.py    # MarsData: fetches raw data from NASA
    ├── commands.py     # Commands: processes and returns sol data
    └── models/
        ├── __init__.py
        └── sol.py      # Sol model
```

---

## Getting Started

1. Clone the repo:
   ```bash
   git clone https://github.com/dimitrilahanas/sol-api.git
   cd sol-api
   ```
2. Install dependencies:
   ```bash
   pip install fastapi uvicorn requests python-dotenv
   ```
3. Get a free API key from [api.nasa.gov](https://api.nasa.gov) and create a `.env` file:
   ```
   NASA_API_KEY=your_key_here
   ```
4. Run the server:
   ```bash
   uvicorn main:app --reload
   ```

---

## Status

Complete and functional.

> **Note:** NASA's InSight mission ended in December 2022, so the dataset is historical and covers the sols InSight recorded.
