###
# Build, tag and push to dockerhub
```sh
docker build . -t php7-fpm
*note*: docker run -it php7-fpm sh
docker tag php7-fpm robkel/php7-fpm
docker push robkel/php7-fpm
```
###
# Steps to create Pods, Services, ConfigMaps
```sh
kubectl create -f ./k8s/php7fpm-rc.yaml
kubectl create -f ./k8s/php7fpm-svc.yaml
kubectl create configmap nginx-config --from-file=k8s/configmap-files
(kubectl create configmap nginx-config --from-file k8s/nginx-conf.yaml)

kubectl create -f ./k8s/my-nginx.yaml
kubectl create -f ./k8s/nginx-svc.yaml
minikube service my-nginx

# ssh into nginx container
kubectl exec -it [pod name] -c my-nginx bash
kubectl exec -it php7-fpm-d58gn -c phpfpm sh
```
