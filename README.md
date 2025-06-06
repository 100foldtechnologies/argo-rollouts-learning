# Canary Deployment Using Argo Rollouts

Canary is one of the most popular and widely adopted techniques of progressive delivery, advanced approach to blue/green. With a  canary deployment, you deploy the new version of the application to a subset of users while the rest continue using the original version.

In canary deployment, where instead of putting entire end-users in danger like in old big-bang deployment, we alternative start releasing our new version of the application to a very small percentage of users and then try to do scrutiny and see if all working as expected and then gradually release it to a larger audience in an Progressive way.

# Benefits of Argo Rollouts for Canary Deployments
**Reduced Risk:** Canary deployments allow you to release updates to a small subset of users first. which reduce the impact of potential issues and reduces the risk of widespread outages.

**Improved User Experience:** Only a small portion of users experience the new changes initially, which reduce the impact of potential bugs or performance issues.

**Flexibility and Control:** You have the flexibility to control the percentage of users receiving the new version at any time.

**Cost-Effective:** initially deploying to a small subset of servers, you can optimize resource usage and only scale up once the new version is verified to be stable.

# How Canary Deployment works Using Argo Rollouts
Argo Rollouts is a Kubernetes controller that manages ReplicaSets, creating, deleting, and scaling them to deploy containerized applications. The Rollout resource specifies the Replica Sets using a pod template from the Deployment.
