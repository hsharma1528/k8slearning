# Some useful kubectl basic and detailed commands  ![](https://visitor-badge.glitch.me/badge?page_id=hsharma1528.k8slearning)

## Short Name for Commands

| Short name           | Full name                    |
| -------------------- | ---------------------------- |
|  csr                 |  certificatesigningrequests  |
|  cs                  |  componentstatuses           |
|  cm                  |  configmaps                  |
|  ds                  |  daemonsets                  |
|  deploy              |  deployments                 |
|  ep                  |  endpoints                   |
|  ev                  |  events                      |
|  hpa                 |  horizontalpodautoscalers    |
|  ing                 |  ingresses                   |
|  limits              |  limitranges                 |
|  ns                  |  namespaces                  |
|  no                  |  nodes                       |
|  pvc                 |  persistentvolumeclaims      |
|  pv                  |  persistentvolumes           |
|  po                  |  pods                        |
|  pdb                 |  poddisruptionbudgets        |
|  psp                 |  podsecuritypolicies         |
|  rs                  |  replicasets                 |
|  rc                  |  replicationcontrollers      |
|  quota               |  resourcequotas              |
|  sa                  |  serviceaccounts             |
|  svc                 |  services                    |


## Change Namespace using kubectl:
  ```
  kubectl config set-context $(kubectl config current-context) --namespace=<namespace name> 
  ```


## Imperitive Commands with examples:

  ### Create a pod:
  ``` kubectl run nginx-pod --image=nginx:alpine ```
  
  ### Create a pod with label:
  ``` kubectl run redis --image=redis:alpine -l tier=db ```
  
  ### Expose a pod:
  ``` kubectl expose pod redis --port=6379 --name=redis-service ```
  
  ### Create a pod and expose is in same command:
  ``` kubectl run httpd --image=httpd:alpine --port=80 --expose ```
  
 ### Create a deployment:
  ``` kubectl create deployment webapp --image=kodekloud/webapp-color ```
 ### Scale a deployment:
  ``` kubectl scale deployment webapp --replicas=3 ```

## Create a yaml file using command:
 ``` kubectl create deployment redis-deploy --image=redis --namespace=dev-ns --dry-run=client -o yaml > deploy.yaml ```
 
## Rolling updates and rollback a deployment in kubernetes
 
   ### Create a deployment
   ``` kubectl apply -f deploy.yaml ``` ( update)
   ### Update image in the deloyment  
   ``` kubect set image deployment/deploy nginx=nginx:1.9.1 ```

   ### Check rollout status of image update
   ``` kubectl rollout status deployment/deploy ```
   ### Check rollout history
   ``` kubectl rollout history deployment/deploy ```
   ### Undo a rollout to previous version
   ``` kubect rollout undo deployment/deploy ```

   ### Undo a rollout to specific version
   ``` kubect rollout undo deployment/deploy --to-revision=<revision no> ```
   
