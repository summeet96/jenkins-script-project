# Simple Notes App
This is a simple notes app built with React and Django.

## Requirements
1. Python 3.9
2. Node.js
3. React

## Installation
1. Clone the repository
```
git clone https://github.com/LondheShubham153/django-notes-app.git
```

2. Build the app
```
docker build -t notes-app .
```

3. Run the app
```
docker run -d -p 8000:8000 notes-app:latest
```

## Nginx

Install Nginx reverse proxy to make this application available

`sudo apt-get update`
`sudo apt install nginx`# django-app


## Shell script for deployment

```
#!/bin/bash

<<task
Deploy a Django app
and handle the code for errors
task
sudo apt-get update
code_clone() {
        echo "cloning code for Django app...."
        git clone https://github.com/LondheShubham153/django-notes-app.git

}

install_requirements() {
        cd django-notes-app
        echo "Installing dependencies..."
        sudo apt-get install docker.io nginx -y docker-compose
}
required_restart() {
        sudo chown $USER /var/run/docker.sock
        #sudo systemctl enable docker
        #sudo systemctl enable nginx
        #sudo systemctl restart docker
}

deploy(){
        docker build -t notes-app .
        docker-compose up -d
        #docker run -d -p 8000:8000 notes-app:latest
}

echo"*************DEPLOYMENT STARTED****************"

if ! code_clone; then
        echo "the directory already exists"
        exit 1
fi

if ! install_requirements; then
        echo "Installation of docker and nginx failed!"
        exit 1
fi

if ! required_restart; then
        echo "System, fault identified during system restart"
        exit 1
fi

if ! deploy; then
        echo "Deployment failed"
        exit 1
fi

echo "***************DEPLOYMENT DONE***************"

```
