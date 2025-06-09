# Let’s Start with Hands-on/Practical of Argo Rollouts with Canary Deployments.

# Prerequisites
Pre-Install Ubuntu 24.04 LTS
Sudo User with admin privileges
2 GB RAM or more
2 CPU / vCPU or more
20 GB free hard disk space or more
Docker / Virtual Machine Manager – KVM & VirtualBox


# Install Argo Rollouts controller on Minikube
Create the namespace for installation of the Argo Rollouts controller

<pre>kubectl create namespace argo-rollouts
kubectl apply -n argo-rollouts -f https://github.com/argoproj/argorollouts/releases/latest/download/install.yaml
</pre>
Now, you will see the controller and other components have been deployed. Wait for the pods to be in the Running state.

<pre>
kubectl get all -n argo-rollouts
</pre>

Install Argo Rollouts Kubectl plugin with curl for easy interaction with Rollout controller and resources with below command.

<pre>
curl -LO https://github.com/argoproj/argo-rollouts/releases/latest/download/kubectl-argo-rollouts-linux-amd64
chmod +x ./kubectl-argo-rollouts-linux-amd64
sudo mv ./kubectl-argo-rollouts-linux-amd64 /usr/local/bin/kubectl-argo-rollouts
kubectl argo rollouts version
</pre>

Argo Rollouts comes with its own GUI as well that you can access with the below command.

<pre>kubectl argo rollouts dashboard </pre>
Now, you can access Argo Rollout console, by accessing http://publicIP:3100 on your browser. You would be presented with UI as shown below.

**Define the Canary Rollout YAML**
Use files in canary deployment

<pre>
kubectl apply -f rollout.yaml
kubectl apply -f ingress.yaml
kubectl apply -f service.yaml
  </pre>

Run the below kubectl command to expose blue-green service to access on browser.

<pre>kubectl port-forward svc/rollouts-demo --address 0.0.0.0 8081:80</pre>
Now, you can access your sample app, by accessing this http://publicIP:8081 on your browser. You will able to see the app as shown below.

You can see the current status of this rollout by running the below command as well.

<pre>kubectl argo rollouts get rollout rollouts-demo</pre>

Now, let’s deploy the Yellow version of the app using canary strategy via command line.

<pre>kubectl argo rollouts set image rollouts-demo rollouts-demo=argoproj/rollouts-demo:yellow </pre>



