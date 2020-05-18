# Hospital Snapshot

Dashboard Tool for Torch

* Refer to individual readme files of the frontend and api in their respective folders.



# Covid19 US Data Visualizer

This project has been built using the AngularJS framework to visualize the COVID19 data subscribed to the [Pomer COVID19 API](https://github.com/pomber/covid19).

You can view the project hosted on Firebase here

https://covidvisualizer-c4fa1.firebaseapp.com/

You can view the Docker containerized project hosted on Google Cloud Platform here

https://visualizer-a3q7pok5ia-uc.a.run.app

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

Clone this repo onto your local drive and then cd into the project folder

#### Clone

Clone this repo to your local machine using https://github.com/laxmanbalajib97/covidVisualizer.git

```
$ cd covidVisualizer
```

#### Runtime required
Make sure you're have npm and the current LTS version nodejs ^12.16.2 installed.

https://nodejs.org/en/download/

NPM should be installed along with nodejs.
Check if NPM is installed using

```
$ npm --version
6.12.4
```
Check your version of nodejs using

```
$ node --version
v12.16.2
```

### Installing

The package.json has the necessary details of the dependencies required for both deployment and development.
Install the dependencies using

```
$ npm install
```

This should have successfully installed the required dependencies.

We'll go ahead and check if AngularJS is successfully installed

```
$ ng --version
Angular CLI: 9.1.2
Node: 12.16.2
OS: darwin x64
```

## Deploy the project for development

To deploy the project on your local host for development purposes use

```
$ ng serve
```

On successfully compiling the project, navigate to http://localhost:4200/ on your web browser.

## Deployment

### Build

Build the project using

```
ng build --prod
```

This should build the project in the directory /dist/covidVisualizer

## Docker Container

Alternatively you can use a Docker image to make your life a little easy.

The dockerfile has the necessary steps needed to pull and build the Docker image

```
$ docker build -t <dockerImageName> .
```

Run the project on the docker container using

```
docker run -it -p 8000:80 --name <dockercontainerName> <dockerImageName>
```
Navigate to http://localhost:8000/ on your web browser.

## Built With

* [NodeJS](https://nodejs.org/en/docs/) - The JS runtime used
* [Angular](https://angular.io/docs) - The frontend web framework used
* [Docker](https://docs.docker.com) - The container framework used
* [ChartJS](https://www.chartjs.org/docs/latest/) - Used to generate charts for visualization

## Authors

* **Laxman Balaji Balasubramanian** - [laxmanbalajib97](https://github.com/laxmanbalajib97)

## Acknowledgments

* [Pomer](https://github.com/pomber/covid19) for his api from which the data is being read
