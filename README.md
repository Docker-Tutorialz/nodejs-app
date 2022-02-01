## `Building the first image Docker based on NodeJS app`

For this basic project, we will use `NodeJS` application to deploy a message on the browser exposing the port to stay visible for us.

## Installation

This installation is based on LINUX Ubuntu, in this case to install please follow the steps below:

```bash
$ apt install nodejs -y
```

## Usage

Ensure you have executed the application locally using the command below:

```bash
$ node app.js
```

After this, please check on your web browser the address `http://192.168.1.100:3000/`. You can able to see the message `Olá MUNDO!` in portuguese.

## Build a Docker image using the NodeJS app

Now we can create a `Dockerfile` to deploy the Docker image:

```dockerfile
FROM node
WORKDIR /src
COPY package*.json .
RUN npm install
COPY . .
EXPOSE 3000
CMD ["node", "app.js"]
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[GNU General Public License v3.0](https://github.com/Docker-Tutorialz/nodejs-app/blob/main/LICENSE)
