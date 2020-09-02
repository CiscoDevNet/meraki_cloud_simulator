# Meraki Cloud Simulator
Locally run Python 3.5+ Flask based application that provides HTTP POST simulations of Location Scanning, WebHook Alerts and Splash Page (Captive Portal) Integrations.

The simulator can be run as a standalone python application or as Docker container in conjunction with all supporting samples (location scanning, webhook alerts, and captive portal).

[Run as Docker Container](#Run-as-Docker-Container)

(##Run-as-Docker-Container)

The webhook simulator and the captive portal simulator use Webex Teams to post updates.  Before starting the application, add in your developer token and room ID  (see: https://developer.webex.com) that you'd like to post notifications to.  Those are added in the wt_vars.env file and will be pulled into the appropriate containters.

```
docker-compose up
```

Head to http://localhost:5001/go to validate simulator is up and running.

To run:

* virtual envrionment:
```
python -m venv simulator
source simulator/bin/activate
```

* Install dependencies
```
pip install -r requirements.txt
```

* Go!
```
python meraki_cloud_simulator.py
```

Navigate to http://localhost:5001/go and select the simulator you'd like to use.

All of the below require a third party application to be running for these simulations to send data to.  Baseline samples can be found at:

* Location Scanning sample receiver
* Webhook Sample receiver
* Captive Portal Sample

## Location Scanning

Enter number of clients and APs for the simulator provide location data, set the location of the desired map and the receiving services url and hit Launch Simulator to run.  Location data for that location, AP and client set will be generated and HTTP Posted to the url provided

## Webhook Alerts

Select the alerts for this service to send and configure the HTTP listening service at the bottom and set as default receiver.  Upon Save, sample alerts will be sent on a 10 second basis>

## Captive portal

Enter the URL for the captive portal to be tested and the continuation URL.  Upon hitting "Simulate WiFi Connection" the service will open a new tab to the captive portal as if your local client was connecting to a Meraki SSID and serving up a captive portal
