# Topcoder Visual Recognition Nodejs Starter Application

  The IBM Watson [Visual Recognition](http://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/visual-recognition.html) service analyzes the visual content of images and videos to understand the scene without any input text describing

## Getting Started

1. Create a Bluemix Account

  [Follow these instruction](http://topcoder.mybluemix.net/signup) to sign up for a new IBM Buemix account, or use an existing account. Watson Services in Beta are free to use.

2. Download and install the [Cloud-foundry CLI](https://github.com/cloudfoundry/cli#downloads) tools

3. Edit the `manifest.yml` file and change the application name by replacing `<your topcoder handle>` with your top coder handle. eg: `foo-fun-watson`
  ```none
applications:
- services:
  - visual-recognition-service
  name: <your topcoder handle>-fun-watson
  command: node app.js
  path: .
  memory: 128M
  ```
  The name you use will determinate your application url initially, e.g. `foo-fun-watson.mybluemix.net`.

4. Connect to Bluemix in the command line tool
  ```sh
  $ cf api https://api.ng.bluemix.net
  $ cf login -u <your user ID>
  ```

5. Create the Visual Recognition service in Bluemix
  ```sh
  $ cf create-service visual_recognition free visual-recognition-service
  ```

6. Push it live!
  ```sh
  $ cf push
  ```

See the full [Getting Started](http://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/doc/getting_started/) documentation for more details, including code snippets and references.

## Running locally
  The application uses [Node.js](http://nodejs.org) and [npm](https://www.npmjs.com) so it assumes you already have it installed. If not, use the above link to install node and npm.

1. Copy the credentials from your `visual-recognition-service` service in Bluemix to `app.js`, you can see the credentials using:

    ```sh
    $ cf env <application-name>
    ```
    Example output:
    ```sh
    System-Provided:
    {
    "VCAP_SERVICES": {
      "visual_recognition": [{
          "credentials": {
            "url": "<url>",
            "password": "<password>",
            "username": "<username>"
          },
        "label": "visual_recognition",
        "name": "visual-recognition-service",
        "plan": "free"
     }]
    }
    }
    ```

    You need to copy `username` and `password`.

2. Go to the project folder in a terminal and run:
    `npm install`
3. Start the application with `node app.js`
4. Open `http://localhost:3000`

## Troubleshooting

To troubleshoot your Bluemix app the main useful source of information are the logs, to see them, run:

  ```sh
  $ cf logs <application-name> --recent
  ```

## License

  This sample code is licensed under Apache 2.0. Full license text is available in [LICENSE](LICENSE).
