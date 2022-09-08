# Deploying Python App to Google Cloud
Deploying to App Engine, Kubernetes Engine and Cloud Run

* To test the program, enter the following command to build a Docker container of the image
`docker build -t <APP-NAME> .`

* To run the Docker image, enter the following command
`docker run --rm -p 8080:8080 <APP-NAME>`

## Deploy to App Engine
App Engine is a completely automated deployment platform. It supports many languages, including Python, Java, JavaScript, and Go. To use it, you create a configuration file and deploy your applications with a couple of simple commands. In this task, you create a file named app.yaml and deploy it to App Engine

1. Paste the following into the file you just created
`runtime: python37`

2. In a project, an App Engine application has to be created. This is done just once using the gcloud app create command and specifying the region where you want the app to be created. Enter the following command
`gcloud app create --region=<PREFERRED-REGION>`

3. Now deploy your app with the following command
`gcloud app deploy --version=one --quiet`

4. From the App Engine Dashboard click on the link to test your program
5. Deploy another version with the following command
`gcloud app deploy --version=two --no-promote --quiet`

## Deploy to Kubernetes Engine
Kubernetes Engine allows you to create a cluster of machines and deploy any number of applications to it. Kubernetes abstracts the details of managing machines and allows you to automate the deployment of your applications with simple CLI commands

1. Navigate to the Kubernetes Engine dashboard and create a cluster
2. In the Connect to the cluster screen, copy the code and enter it on your taminal to connect to the cluster
3. To test your connection, enter the following command (This command simply shows the machines in your cluster)
`kubectl get nodes`

4. Add a file named kubernetes-config.yaml (the template can be found in this repo)
