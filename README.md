# Supply Chain Tracking Using Kafka, Flask, and Dash
## Overview:
This project is a real-time supply chain tracking system designed to visualize truck locations on a live map. It demonstrates the integration of IoT and logistics concepts by leveraging Apache Kafka for real-time data streaming and Dash for live visualization. The system aims to enhance supply chain efficiency by providing stakeholders with instant updates on truck movements.
## Components

- **Producer (Truck Location Generator)**
  - Simulates multiple trucks by generating random geographic coordinates (latitude and longitude).
  - Streams real-time truck location data to a Kafka topic (`TruckLocations`).
  - Each truck is assigned to a unique Kafka partition for efficient processing.
  - **Libraries used:**
    - `KafkaProducer` (Apache Kafka)
    - `json`
    - `threading`
    - `random`

- **Consumer (Live Map Dashboard)**
  - Consumes truck location data from the Kafka topic.
  - Visualizes truck positions on an interactive map using Folium and Dash.
  - Periodically updates the map to reflect the latest truck positions.
  - **Libraries used:**
    - `KafkaConsumer` (Apache Kafka)
    - `Dash` and `dash_bootstrap_components`
    - `Folium`
    - `base64` for rendering HTML maps in Dash.



- **Flask Application:**
  - Flask is used to create a simple web server that serves the live map to users.
  - The server-side Flask application integrates with Dash to provide real-time map updates based on incoming truck data.
  - The application runs continuously, and as new data is received from Kafka, the map is updated accordingly.

- **Dash and Map Visualization:**
  - Dash, a Python framework for building analytical web applications, is used for the front-end interface.
  - Folium, a Python library for visualizing geographic data, generates the map with truck positions.
  - The map is embedded in an HTML page (map.html) and is updated in real-time with the latest truck locations.
  - A periodic callback (using dcc.Interval) refreshes the map display every second to reflect the latest data.

- **map.html:**
  - The map.html file is an auto-generated HTML file that contains the visual representation of the map with truck markers.
  - Each truck's location is represented by a marker on the map, and the map updates dynamically as new location data is received.
  - The map is rendered inside the Dash app as an HTML iframe, allowing it to be updated seamlessly without refreshing the entire page.

## How It Works

- **Producer**
  - Generates and sends truck location data in real time to the Kafka topic.
- **Consumer**
  - Listens to the Kafka topic, retrieves truck data, and displays it on a live map interface.
- **Map Updates**
  - Automatically updates at regular intervals to provide an up-to-date view of truck movements.

## Applications in Supply Chain

- **Fleet Tracking**
  - Monitor the real-time positions of vehicles in transit.
  - Identify deviations from planned routes.
- **Operational Efficiency**
  - Reduce delays by identifying deviations in planned routes.
- **Data-Driven Insights**
  - Use historical truck data for route optimization and performance analytics.

