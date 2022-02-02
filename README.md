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

## Build a Docker image using the nodejs image

Now we can create a `Dockerfile` to deploy the Docker image:

```dockerfile
FROM node
WORKDIR /src
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["node", "app.js"]
```

- After this step, please proceed wth the command below:

```bash
$ docker image build -t amauryborgesouza/nginx-apps:v1 .
```

- Check if the image is listed:

```bash
$ docker image ls
REPOSITORY                    TAG       IMAGE ID       CREATED         SIZE
amauryborgesouza/nginx-apps   v1        a3f7a1b38eed   5 seconds ago   999MB
```

- Now you can able to run the container:

```bash
$ docker container run -d -p 3000:3000 amauryborgesouza/nginx-apps:v1
```

- Push the image have created to Dockerhub:

```
$ docker push  amauryborgesouza/nginx-apps:v1
The push refers to repository [docker.io/amauryborgesouza/nginx-apps]
b4f3dcccf053: Pushed
7bc1a6ddfb60: Pushed
ab068f044e12: Pushed
40593d78553b: Pushed
55e375d8b397: Mounted from library/node
b72a59a07ced: Mounted from library/node
784fcc2e440c: Mounted from library/node
884b130cf8e9: Mounted from library/node
204e42b3d47b: Mounted from library/node
613ab28cf833: Mounted from library/node
bed676ceab7a: Mounted from library/node
6398d5cccd2c: Mounted from library/node
0b0f2f2f5279: Mounted from library/node
v1: digest: sha256:fd856df411a18a0c9a13e894163b66d7575d31dcab3ea7e7e10748383c7492b5 size: 3051
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[GNU General Public License v3.0](https://github.com/Docker-Tutorialz/nodejs-app/blob/main/LICENSE)
