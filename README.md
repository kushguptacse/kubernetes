# kubernetes
For notes refer kubernetesNotes.doc

# requirements
kubernetes must be installed. it comes with docker desktop by default.

# voting app
1. contains all the definition files like deployment/pod/service.
2. voting and result application are 2 front end microservices. voting is used to vote between cat and dog. and result is used to show voting result.
3. voting uses redis to store vote.
4. worker takes data from redis and store it to postgres.
5. postgres is db to store voting records.
6. result reads data from postgres and display on ui.

# kubectl commands
kubectl apply -f voting-app-deploy.yaml
kubectl apply -f redis-deploy.yaml
kubectl apply -f postgres-deploy.yaml
kubectl apply -f worker-deploy.yaml
kubectl apply -f result-app-deploy.yaml
kubectl apply -f redis-service.yaml
kubectl apply -f voting-app-service.yaml
kubectl apply -f postgres-service.yaml
kubectl apply -f result-app-service.yaml

#access application
kubectl get all 
1.it will give status of all application.
2. if all are fine. i.e. pods,rs,deployments, service. now inspect each pod to check node ip.
kubectl describe pod result-app-deploy-6cb79db456-xl9vz |grep -i Node

now uses ipOfNode:30004 and ipOfNode:30005 to access voting and result application.


