`docker-compose -f <compose file>`
- this is used if the compose file is not in the same directory as where you are executing the command

`docker-compose down -v`
- down the container along with its volumes

`Dockerfile`
- you do stuff to the base image, therefore you have to rebuild an image after you change a docker file
- this is where you can install stuff to the base image
- check dockerhub for images that are available

`entrypoint.sh`
- this is the first thing that  the image will do when it is started, you can add your start-up scripts here

```
cp docker/entrypoint.sh . 
chmod +x entrypoint.sh
docker build -t <tag> -f <docker file path> .
docker images
source .env
envsubst < docker/docker-compose.tmpl > docker-compose.yaml
docker compose up -d
```
