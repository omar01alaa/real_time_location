# Real-Time Truck Location Tracking Using Kafka, Flask, and Dash
## Overview:
This project demonstrates a real-time system for tracking the location of multiple trucks on a map. The system uses Apache Kafka for message brokering, where a producer sends the location data of trucks, and a consumer receives this data, updating the truck's position on a live map. The map is displayed using a web interface powered by Flask and Dash, allowing users to visualize truck movements in real-time.
## Components

### Producer:
The producer is a Python script that simulates trucks' movements by generating random latitude and longitude coordinates at regular intervals.
Each truck's location data is sent to a Kafka topic named TruckLocations.
The producer can simulate multiple trucks, each identified by a unique truck_id.

### Kafka:
Apache Kafka is used as the messaging system to handle the streaming data between the producer and consumer.
Kafka ensures that the location data for each truck is sent and received reliably.
The data is published to a Kafka topic (TruckLocations), with each truck's data potentially assigned to a separate partition, allowing parallel processing.

### Consumer:
The consumer is a Python application that listens to the TruckLocations Kafka topic.
It receives the location data for each truck in real-time and updates the truck's position on the map.
The consumer uses a separate thread to continuously receive data, ensuring the map updates without interruptions.

### Flask Application:
Flask is used to create a simple web server that serves the live map to users.
The server-side Flask application integrates with Dash to provide real-time map updates based on incoming truck data.
The application runs continuously, and as new data is received from Kafka, the map is updated accordingly.

### Dash and Map Visualization:
Dash, a Python framework for building analytical web applications, is used for the front-end interface.
Folium, a Python library for visualizing geographic data, generates the map with truck positions.
The map is embedded in an HTML page (map.html) and is updated in real-time with the latest truck locations.
A periodic callback (using dcc.Interval) refreshes the map display every second to reflect the latest data.

### map.html:
The map.html file is an auto-generated HTML file that contains the visual representation of the map with truck markers.
Each truck's location is represented by a marker on the map, and the map updates dynamically as new location data is received.
The map is rendered inside the Dash app as an HTML iframe, allowing it to be updated seamlessly without refreshing the entire page.
