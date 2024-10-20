Here's a comprehensive README file for your weather monitoring system project. It covers the build instructions, design choices, dependencies, and additional information.

---

# Real-Time Weather Monitoring System

## Overview

This project is a **Real-Time Weather Monitoring System** that retrieves live weather data from OpenWeatherMap API for various cities, stores the data in a local SQLite database, and provides real-time alerts for abnormal weather conditions. Additionally, it visualizes temperature trends for selected cities. The system is built using Flask for the backend and a simple HTML/CSS/JavaScript front end to display the data.

For visualization, random data has been added for the past 30 days to simulate historical weather trends.

## Features

1. **Real-Time Weather Monitoring:** Fetches real-time weather data for six major cities (Delhi, Mumbai, Chennai, Bangalore, Kolkata, and Hyderabad).
2. **Temperature Alerts:** Raises an alert if a city's temperature exceeds a predefined threshold (35°C).
3. **Temperature Trend Visualization:** Users can view temperature trends for a selected city over the past 30 days.
4. **Automated Data Collection:** Weather data is collected periodically and stored in a SQLite database.
5. **Cross-Origin Resource Sharing (CORS) Support:** Allows API access from different domains.

## Design Choices

- **Backend Framework:** Flask was chosen for its simplicity and ease of integration with RESTful services.
- **Database:** SQLite is used as a lightweight, file-based database to store weather data summaries.
- **API Integration:** OpenWeatherMap API is used to fetch real-time weather data.
- **Frontend:** A basic HTML and Bootstrap-based interface was used for a simple and responsive design.
- **Visualization:** Matplotlib is used to generate temperature trend graphs, which are served to the frontend as base64-encoded images.

## Prerequisites

- **Python 3.x**
- **SQLite**
- **Flask**
- **Matplotlib**
- **Requests**
- **OpenWeatherMap API Key** (You can get one by registering on [OpenWeatherMap](https://home.openweathermap.org/users/sign_up))
- **Docker or Podman (Optional)** if you want to containerize the application.

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/weather-monitoring-system.git
cd weather-monitoring-system
```

### 2. Install Dependencies

Ensure that you have Python 3.x installed, then run:

```bash
pip install -r requirements.txt
```

The `requirements.txt` should contain:
```
Flask==2.0.1
requests==2.25.1
matplotlib==3.4.2
apscheduler==3.7.0
flask-cors==3.0.10
```

### 3. Setup OpenWeatherMap API Key

Replace the placeholder `API_KEY` in the `app.py` file with your actual OpenWeatherMap API key.

```python
API_KEY = 'your_openweathermap_api_key_here'
```


### 4. Run the Application

```bash
python app.py
```

By default, the app runs in debug mode on `http://127.0.0.1:5000/`. You can open this URL in your browser to access the application.

### 6. Fetch Real-Time Weather Data

To simulate historical data for temperature trends, random data for the past 30 days has been added. For real-time monitoring, weather data will be fetched every 24 hours and stored in the database.

You can manually trigger weather data collection by running:

```bash
python -c 'from app import collect_weather_data; collect_weather_data()'
```

er build -t weather-monitoring-system .
```


## API Endpoints

- **`/api/current_weather`:** Fetches real-time weather data for all cities.
- **`/api/check_alerts`:** Checks for temperature alerts if any city exceeds the predefined threshold.
- **`/api/visualize_trends/<city>`:** Generates a temperature trend graph for the selected city.

## Visualization

The application provides a dropdown menu where users can select a city and view the temperature trends for the last 30 days. Random data has been added for this purpose to allow users to visualize trends even if there is no historical data available.

## Cron Job / Scheduler

The system automatically collects weather data every 24 hours using the `apscheduler` library. If you run the application continuously, it will keep updating the weather database.

## Conclusion

This weather monitoring system can easily be extended to include more cities, different weather parameters, or advanced visualization. It serves as a lightweight solution for tracking and visualizing weather trends in real-time.
