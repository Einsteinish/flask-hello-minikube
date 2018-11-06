# Flask with Kubernetes (Minikube)

$ eval $(minikube docker-env) 

$ docker build -t dockerbogo/flask-hello-kubernetes:2.0.0 . 
$ docker push dockerbogo/flask-hello-kubernetes:2.0.0 
 
 
$ kubectl apply -f deployment.yml  
deployment.extensions/flask-hello-kubernetes-deployment created 

$ kubectl get deployment 
NAME                                DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE 
flask-hello-kubernetes-deployment   1         1         1            1           9s 

$ kubectl apply -f service.yml 
service/flask-hello-kubernetes-service created 


$ kubectl get service 
NAME                             TYPE           CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE 
flask-hello-kubernetes-service   LoadBalancer   10.103.44.203    &lt;pending&gt;     80:30148/TCP     1m 

$ minikube service flask-hello-kubernetes-service --url 
http://192.168.99.100:30148 

Ref: 
[Docker & Kubernetes : minikube](https://www.bogotobogo.com/DevOps/Docker/Docker_Kubernetes_Minikube.php)

