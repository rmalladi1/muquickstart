# muquickstart
Steps
#Install mu

curl -s https://getmu.io/install.sh | sudo sh

#Create a new git repo and clone  

git clone git@github.com:my-github-user/my-app && cd my-app

#Create a webpage - 
vi index.html

<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
  </head>
  <body>Hello World!</body>
</html>

#Create Dockerfile - vi Dockerfile
FROM nginx
COPY index.html /usr/share/nginx/html/index.html

#Initialize the mu.yml and buildspec.yml files: 

mu init --port 80 --env

#Update the mu.yml to use / for the healthEndpoint:

service:
  name: extension
  port: 80
  healthEndpoint: /
  pathPatterns:
  - /*
  pipeline:

#Commit and push: 
git add --all && git commit -m "mu init" && git push

# create the env
mu env up -A

#Create the pipeline: 
mu pipeline up

#Enter your GitHub Token when prompted (creation of OAuth GitHub token guide here)

#Show the status of the service: 
mu svc show

#Delete all resources in AWS: 
mu purge
