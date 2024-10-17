# eudi component deployment
This repository contains the 'docker-compose.yml' files to deploy eudi components for verifying and issuing

## Quickstart
1. Clone this repo
2. Clone the `eudi-web-server`, `eudi-srv-web-verifier-endpoint-23220-4-kt` and `eudi-srv-web-issuing-eudiw-py`  repos and place them in this repo's directory
  * To build a local docker image of the verifier endpoint, in the corresponding repo execute `./gradlew bootBuildImage`
  * For the issuing service, replace all instances of `https://14b0a149d4b4.ngrok.app` in the code's files  with the current public URL that it'll be running on.
  * For the issuing service, copy `app/app_config/__config_secrets.py` to `app/app_config/config_secrets.py`
3. Configure docker-compose.dev.yml according to your local setup (see below)
4. To locally deploy the verifying service, run
```docker compose -f docker-compose.dev.yml up```

## docker-compose.dev.yml config
* The environment variables VERIFIER_PUBLICURL for the verifier component and HOST_API for verifier-ui need to match. The URL should set to the public URL of the verifier component (i.e. the component running on port 8080).
* Ensure that the image name for the verifier component corresponds to the image built thrugh executing the gradlew command

## ngrok
Part of the UX flow requires the scanning of a QR code using the wallet app on your phone, but your phone likely can't communicate with your locally hosted services by default. One solution is to use a proxy service such as ngrok, an example config file for which is included (ngrok.yml.example).

1. To get started, create an account.
2. You authentication token will be shown on the dashboard after you login.
3. Copy the ngrok.yml.example file and configure it to match the ports the different services are running on.
4. After copying the file, you can start ngrok with the following command:
```ngrok start --config=ngrok.yml --all```

After ngrok has started, you can update the docker-compose.dev.yml file with the new ngrok URLs.

For the issuing service, replace all instances of `https://14b0a149d4b4.ngrok.app` with the current public URL that it'll be running on.

