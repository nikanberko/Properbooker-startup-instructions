# Properbooker-startup-instructions
How to start and test the Properbooker application:

## About
Properbooker is a microservice based multiplatform application which simplifies the process
of registering tourists in accomodation units. Since 2015. all tourists which reserve an
accomodation unit in Croatia need to be registered via the e-visitor system. This system prompts
the apartment owner to enter a lot of information about the tourists into the system by hand,
which can be quite tiresome when accomodating larger groups of guests. This information is
later sent to the Ministry of internal affairs for validation. This application gives a
solution to this problem by providing an interface for identification document scanning with
Google Vision API and automatic text field input. Alongside ID scanning,
this application provides an interface for PDF cost estimation generation.

## How to start the application:
### Prerequisites:
  You will need to install these packages and programs beforehand:
  * NPM, node.js, JAVA 17 with appropriate JDK, Docker and Docker Compose, ngrok
  * A code editor, preferably Intellij iDEA
  * Expo Go application for real-time React Native development on your mobile device: https://expo.dev/expo-go

### Startup process
1. Open up the following Spring Boot projects in the following order (it's important to start all the microservices before the Eureka server and API Gateway):
  * Apartment Mangement (navigate to the Docker folder and run: docker compose up -d to start the PostgreSQL database and admin panel),
    install dependencies from POM file
  * ProperbookerJWTAuth (navigate to the Docker folder and run: docker compose up -d to start the PostgreSQL database and admin panel),
    install dependencies from POM file
  * mrz-spring,
    install dependencies from POM file
  * PDFGenerator,
    install dependencies from POM file
  * MOCK e-visitor,
    install dependencies from POM file
  * Properbooker discovery service,
    install dependencies from POM file
  * Properbooker API Gateway,
    install dependencies from POM file

2. The ProperbookerJWTAuth will create a test account with username: admin and password admin, this will be important later.
3. Open the ProperbookerFrontend project and run npm install to install all the dependencies.
4. Open the ngrok directory and run the bash command ./ngrok http 8765, ngrok is a tool for tunneling your local ports to the public domain. Esentially making       your computer a server. 8765 is the port number of the API Gateway service through which you can access all of the other endpoints. We need to do this so the     application on your mobile device can actually access the endpoints from your computer.
5. Inside the React Native app, replace all URLs which use ngrok to the new generated ngrok address. These tunnelling addresses are active for two hours.
6. Put your Google Vision API key in the URL for text annotation.
7. Run npm start - this will start up the React Native application.
8. After starting the application, a QR code will be generated in the terminal, scan it with the Expo Go app and test the app. 

