## cli
```sh
PROJECT_ID="online-boutique-demo"
gcloud services enable container.googleapis.com --project ${PROJECT_ID}

git clone https://github.com/GoogleCloudPlatform/microservices-demo.git
cd microservices-demo

ZONE=us-central1-b
gcloud container clusters create onlineboutique \
    --project=${PROJECT_ID} --zone=${ZONE} \
    --machine-type=e2-standard-2 --num-nodes=4 --disk-size=60

kubectl apply -f ./release/kubernetes-manifests.yaml

kubectl get pods

kubectl get service frontend-external | awk '{print $4}'

gcloud container clusters delete onlineboutique \
    --project=${PROJECT_ID} --zone=${ZONE}
```