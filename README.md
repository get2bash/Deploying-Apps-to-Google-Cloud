# Deploying Python App to Google Cloud
Deploying to App Engine, Kubernetes Engine and Cloud Run

* To test the program, enter the following command to build a Docker container of the image
`docker build -t <APPNAME> .`

* To run the Docker image, enter the following command
`docker run --rm -p 8080:8080 <APP NAME>`

## Deploy to App Engine
App Engine is a completely automated deployment platform. It supports many languages, including Python, Java, JavaScript, and Go. To use it, you create a configuration file and deploy your applications with a couple of simple commands. In this task, you create a file named app.yaml and deploy it to App Engine.

1. Paste the following into the file you just created
`runtime: python37`

2. In a project, an App Engine application has to be created. This is done just once using the gcloud app create command and specifying the region where you want the app to be created. Enter the following command
`gcloud app create --region=<PREFERRED REGION>`

3. Now deploy your app with the following command
`gcloud app deploy --version=one --quiet`

4. From the App Engine Dashboard click on the link to test your program
5. Deploy another version with the following command
`gcloud app deploy --version=two --no-promote --quiet`

## Deploy to Kubernetes Engine
Kubernetes Engine allows you to create a cluster of machines and deploy any number of applications to it. Kubernetes abstracts the details of managing machines and allows you to automate the deployment of your applications with simple CLI commands.

1. Navigate to the Kubernetes Engine dashboard and create a cluster.
2. In the Connect to the cluster screen, copy the code and enter it on your taminal to connect to the cluster.
3. To test your connection, enter the following command (This command simply shows the machines in your cluster)
`kubectl get nodes`

4. Add a file named kubernetes-config.yaml (the template can be found in this repo)
5. To use Kubernetes Engine, you need to build a Docker image. Enter the following commands to use Cloud Build to create the image and store it in Container Registry
`gcloud builds submit --tag gcr.io/$DEVSHELL_PROJECT_ID/<APP NAME>:v0.1 .`

6. Highlight your image name and copy it to the clipboard. Paste that value in the kubernetes-config.yaml file, overwriting the string <YOUR IMAGE PATH HERE>
7. Enter the following Kubernetes command to deploy your application
`kubectl apply -f kubernetes-config.yaml`

8. Type the following command to see whether instance(s) have been created (Make sure all the pods are ready. If they aren't, wait a few seconds and try again)
`kubectl get pods`

9. A load balancer was also added in the configuration file. Type the following command to see whether it was created
`kubectl get services`

10. When you have an external IP, open a browser tab and make a request to it.

## Deploy to Cloud Run
Cloud Run simplifies and automates deployments to Kubernetes. When you use Cloud Run, you don't need a configuration file. You simply choose a cluster for your application. With Cloud Run, you can use a cluster managed by Google, or you can use your own Kubernetes cluster.

1. To use Cloud Run, you need to build a Docker image. In Cloud Shell, enter the following commands to use Cloud Build to create the image and store it in Container Registry
`gcloud builds submit --tag gcr.io/$DEVSHELL_PROJECT_ID/<APP NAME>:v0.1 .`

2. When the build completes, in the Navigation menu, click Cloud Run
3. Click Create service. This enables the Cloud Run API
4. Click the Select link in the Container image URL text box. In the resulting dialog, expand cloud-run-image and select the image listed. Then click Select
5. Complete the other configs as desired then click create.


# Cheers!
































