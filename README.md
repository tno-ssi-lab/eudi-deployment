# eudi component deployment
This repository contains the 'docker-compose.yml' files to deploy eudi components for verifying

## Quickstart
1. Clone this repo
2. Clone the 'eudi-web-server' and 'eudi-srv-web-verifier-endpoint-23220-4-kt' repos and place them in this repo's directory
3. To locally deploy the verifying service, run
'''docker compose -f docker-compose.dev.yml up'''

## ngrok
Part of the UX flow requires the scanning of a QR code using the wallet app on your phone, but your phone likely can't communicate with your locally hosted services by default. One solution is to use a proxy service such as ngrok, an example config file for which will be added later.
