# ecr

there is a limit of 6 variables to fargate. as confluence needs at least 7 we need to create a new image with variables attached to the image.

## create and upload image:

create ecr to upload to (copy repositoryUri):

`aws ecr create-repository --repository-name confluence`

get key and let docker login to ecr (copy and paste back the output to connect docker to ecr):

`(aws ecr get-login --no-include-email)`

create docker image locally:

`docker build -rm -t myconfluence .`

docker tag myimage 

docker push 
