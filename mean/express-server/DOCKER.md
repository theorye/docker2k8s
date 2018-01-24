# We can then build the image and run a container based on the image with.

$ docker build -t express-server:dev .
$ docker run -d --name express-server -p 3000:3000 express-server:dev
$ docker stop express-server

# Assuming we had a MongoDB image already, we'd run a container based on the image with
$ docker run -d --name mongodb -p 27017:27017 mongo

The image name in this instance is mongo, the last parameter, and the container name will be mongodb.

$ docker stop mongodb

# Pushing to GCLOUD

docker build -t gcr.io/[PROJECT_ID]/express-server:v1 .

docker run -d -p 3000:3000 gcr.io/[PROJECT_ID]/express-server:v1
gcloud docker -- push gcr.io/[PROJECT_ID]/express-server:v1

kubectl run express-server --image=gcr.io/[PROJECT_ID]/express-server:v1 --port=3000
