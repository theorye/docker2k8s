 docker-compose up --build

 The --build flag tells docker compose that we've made changes and it needs to do a clean build of our images.

#Building Docker Images for google

 project-id [PROJECT_ID]
docker build -t gcr.io/[PROJECT_ID]/angular-client:v1 .

docker run -d -p 4200:4200 gcr.io/[PROJECT_ID]/angular-client:v1
gcloud docker -- push gcr.io/[PROJECT_ID]/angular-client:v1