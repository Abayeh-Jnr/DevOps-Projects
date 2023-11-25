# BASIC COMMANDS IN KUBERNETES
- We would be making use of minkube to run our kubernetes commands
- Open any terminal of your choice
- Ensure your docker desktop is running
    - Ensure minikube is properly installed and start it with docker as its driver
        - `minikube start  --driver=docker`
        ![Step-1](./images/Step-1.PNG)
    - Open kubernetes via minkube
        - `minikube dashboard`
        ![Step-2](./images/Step-2.PNG)
    - Create a deployment
        - `kubectl create deployment kubernetes-bootcamp --image=gcr.io/google-samples/kubernetes-bootcamp:v1`
        - To view your deployments
        - `kubectl get deployments`
        ![Step-3](./images/Step-3.PNG)
        - Check your kubernetes dashboard
        ![Step-4](./images/Step-4.PNG)
        - Expose our application publicly
            - `kubectl expose deployment/kubernetes-bootcamp --type="NodePort" --port 8080`
            ![Step-5](./images/Step-5.PNG)
            - Check your deployments as containers on docker desktop
            ![Step-6](./images/Step-6.PNG)
    - Scale your deployment to 6 replicas
        - `kubectl scale deployments/kubernetes-bootcamp --replicas=6`
        ![Step-7](./images/Step-7.PNG)
        ![Step-8](./images/Step-8.PNG)
    - Update the version of your deployment to version 4
        - `kubectl set image deployments/kubernetes-bootcamp kubernetes-bootcamp=jocatalin/kubernetes-bootcamp:v2`
        ![Step-9](./images/Step-9.PNG)
    - Stop and delete your deployment
        - `minikube stop`
        - `minikube delete`
        ![Step-10](./images/Step-10.PNG)
        ![Step-11](./images/Step-11.PNG)
