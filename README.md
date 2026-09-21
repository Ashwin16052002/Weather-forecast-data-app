# 🌦️ Weather Forecast Data App

A simple and interactive **weather forecasting web application** built with Python and Streamlit.

The application uses the **OpenWeatherMap API** to retrieve forecast data for a selected location. Users can choose the number of forecast days and visualize either the **temperature** or **sky conditions** through an easy-to-use Streamlit interface.

## ✨ Features

* 🌍 Search weather forecasts by location
* 📅 Select between **1 and 5 forecast days**
* 🌡️ View temperature forecasts
* 📈 Display temperature changes using an interactive Plotly line chart
* ☁️ View sky/weather conditions using weather images
* 🌧️ Supports weather conditions such as Clear, Clouds, Rain, and Snow
* 🖥️ Interactive Streamlit web interface
* 🔌 Uses live data from the OpenWeatherMap API

The current application allows forecast selection from 1 to 5 days and provides Temperature and Sky viewing options.

## 🛠️ Technologies Used

* **Python** – Core programming language
* **Streamlit** – Web application framework
* **Requests** – API requests
* **OpenWeatherMap API** – Weather forecast data
* **Plotly Express** – Interactive temperature visualization

The repository's `requirements.txt` includes Streamlit, Plotly, Requests, Pandas and their supporting dependencies.

## 📂 Project Structure

```text
Weather-forecast-data-app/
│
├── images/
│   ├── clear.png
│   ├── cloud.png
│   ├── rain.png
│   └── snow.png
│
├── main.py
├── backend.py
├── requirements.txt
├── .gitignore
└── README.md
```

## ⚙️ How It Works

```text
             User
               │
               ▼
       Enter Location
               │
               ▼
       Select Forecast Days
          (1 - 5 days)
               │
               ▼
       Select Data to View
          ┌────┴────┐
          │         │
     Temperature   Sky
          │         │
          ▼         ▼
      Plotly      Weather
       Chart       Images
          │         │
          └────┬────┘
               │
               ▼
       Streamlit Interface
```

### 1. Enter a Location

The user enters a city or location into the Streamlit text input.

```python
place = st.text_input("Place: ")
```

### 2. Select Forecast Days

The application provides a slider from **1 to 5 days**:

```python
days = st.slider(
    "Forcast days",
    min_value=1,
    max_value=5
)
```

### 3. Fetch Weather Data

The frontend calls the `get_data()` function from `backend.py`.

```python
filtered_data = get_data(place, days)
```

The backend sends a request to the OpenWeatherMap forecast API and retrieves the forecast data.

### 4. Process Forecast Data

The backend selects the required number of forecast entries based on the requested number of days.

Since the OpenWeatherMap forecast response provides multiple forecast points per day, the application uses:

```python
no_values = 8 * forecast_days
```

to determine how many forecast entries to return.

### 5. Display Temperature

When **Temperature** is selected, the application extracts the temperature and date/time values and creates a Plotly line chart.

```python
figure = px.line(
    x=dates,
    y=temperature,
    labels={
        "x": "Date",
        "y": "Temperature (c)"
    }
)
```

### 6. Display Sky Conditions

When **Sky** is selected, the application maps weather conditions to corresponding images.

```python
images = {
    "Clear": "images/clear.png",
    "Clouds": "images/cloud.png",
    "Rain": "images/rain.png",
    "Snow": "images/snow.png"
}
```

The appropriate images are then displayed in the Streamlit application.

## 🔑 OpenWeatherMap API Key

The application requires an **OpenWeatherMap API key**.

In `backend.py`, the API key is defined as:

```python
API_KEY = "YOUR_API_KEY_HERE"
```

Replace the placeholder with your own OpenWeatherMap API key.

### 🔐 Security Recommendation

Do **not** commit your real API key to GitHub.

For a more secure implementation, use an environment variable or Streamlit secrets instead of placing the API key directly in the source code.

## 🚀 Installation

### Prerequisites

Make sure Python 3.x is installed.

Check your Python version:

```bash
python --version
```

### Clone the Repository

```bash
git clone https://github.com/Ashwin16052002/Weather-forecast-data-app.git
```

Navigate to the project:

```bash
cd Weather-forecast-data-app
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

The repository includes a dependency list in `requirements.txt`.

## ▶️ Running the Application

Start the Streamlit application with:

```bash
streamlit run main.py
```

Streamlit will provide a local URL where you can open the application in your browser.

## 🖥️ Using the Application

After launching the application:

### Step 1

Enter a city name.

Example:

```text
Chennai
```

### Step 2

Select the number of forecast days using the slider.

```text
1 ───────────── 5
```

### Step 3

Choose what you want to view:

```text
Temperature
Sky
```

### Step 4

The application displays the requested forecast information.

For **Temperature**, you will see an interactive Plotly chart.

For **Sky**, you will see weather-condition images.

## 📊 Example

For a location such as:

```text
Chennai
```

and:

```text
Forecast Days: 3
Data: Temperature
```

the application retrieves the forecast data and displays the temperature trend over the selected period.

## 📁 Main Components

### `main.py`

The Streamlit frontend of the application.

Responsibilities include:

* Creating the user interface
* Accepting the location
* Selecting forecast days
* Selecting Temperature/Sky view
* Creating the Plotly temperature chart
* Displaying weather images

### `backend.py`

Handles communication with the OpenWeatherMap API.

Responsibilities include:

* Sending API requests
* Receiving weather forecast data
* Filtering forecast entries
* Returning the processed data to the Streamlit application

### `images/`

Contains the weather-condition images used when the **Sky** option is selected.

## 💡 Future Improvements

Possible improvements for future versions:

* [ ] Secure API key using environment variables
* [ ] Add current weather information
* [ ] Add humidity information
* [ ] Add wind speed
* [ ] Add weather icons directly from the API
* [ ] Add precipitation information
* [ ] Add minimum and maximum temperatures
* [ ] Add sunrise and sunset times
* [ ] Add more forecast visualization options
* [ ] Add error handling for invalid locations
* [ ] Add loading indicators
* [ ] Add responsive styling
* [ ] Deploy the application using Streamlit Community Cloud

## 📚 Learning Outcomes

This project demonstrates practical experience with:

* Python web application development
* Streamlit
* REST API integration
* JSON data processing
* API-based data retrieval
* Interactive data visualization
* Plotly
* Frontend/backend separation
* Handling external API data

## 👨‍💻 Author

**Ashwin V**

GitHub:
https://github.com/Ashwin16052002

LinkedIn:
https://www.linkedin.com/in/ashwin-v-5124992a9/

## 📜 License

This project is intended for educational and personal use.

---
