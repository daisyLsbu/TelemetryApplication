# TelemetryApplication
Application to get the telemetry information, developed in python.
psutil library for system resource information for foot-printing application.
dockerstat api for the resources related to all the containers.
RTT data between the application host and the list of other hosts in the network.

# Setup:
1. Install psutil and dockerpy libraries using pip install command.
2. Run the application with python app.py <port>.
Example : python app.py 5000
3. Open a web browser and go to http://localhost:<port>/ to see the UI

### Description
This is an example project that showcases how you can use the `psutil`
library to send metrics from your applications to a monitoring server written
in any language.

The included `app.py` file shows all the available apis 

### Running the Example
Use the setup and build script before starting the application or launch script can be used to run all 3 script at once.

use the following endpoints depending on the need:
/devicedetails : for the server metric
/containers : for docker metrics
/combined : for combined metrics
/rtt with host list in request body: to get rtt data in network 

