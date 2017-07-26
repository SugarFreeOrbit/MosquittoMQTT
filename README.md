How to setup a Mosquitto MQTT broker with TLS/SSL protection using self-signed certificates and connect it to Mongoose Os
=========================================================================================================================

1. Generate all required certificates and keys (CA, server and client) using [generate-CA.sh](https://github.com/owntracks/tools/blob/master/TLS/generate-CA.sh)
2. Add the following parameters to your mosquitto configuration file:
  require_certificates true
  cafile <path to your CA certificate>
  certfile <path to your server certificate>
  keyfile <path to the key for your server certificate>
  port 8883
3. Make the following changes to your Mongoose OS MQTT  configuration:
  ```json
  "mqtt": {
    "enable": true,
    "server": "YOUR_IP:8883",
    "ssl_cert": "YOUR_CLIENT_CERTIFICATE.crt",
    "ssl_key": "YOUR_CLIENT_KEY.key",
    "ssl_ca_cert": "YOUR_CA_CERTIFICATE.crt",  
  ```
