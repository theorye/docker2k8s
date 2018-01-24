
# docker build -t <image_tag>:<tag> <directory_with_Dockerfile>
-t is a shortform of --tag, and refers to the name or tag given to the image to be built. In this case the tag will be angular-client:dev.

The . (dot) at the end refers to current directory. Docker will look for the Dockerfile in our current directory and use it to build an image.

ex: 
docker build -t angular-client:dev .

# Now that the image is built, we can run a container based on that image, using this syntax

$ docker run -d --name <container_name> -p <host-port:exposed-port>  <image-name>

ex:
docker run -d --name angular-client -p 4200:4200 angular-client:dev

# Stop

docker stop angular-client

# Pushing to GCLOUD
docker build -t gcr.io/[PROJECT_ID]/angular-client:v1 .

docker run -d -p 4200:4200 gcr.io/[PROJECT_ID]/angular-client:v1
gcloud docker -- push gcr.io/[PROJECT_ID]/angular-client:v1

# Pushing to GCLOUD

kubectl run angular-client --image=gcr.io/[PROJECT_ID]/angular-client:v1 --port=4200

kubectl get deployments

kubectl logs <POD-NAME>

kubectl expose deployment angular-client --type="LoadBalancer"

https://kubernetes-v1-4.github.io/docs/hellonode/