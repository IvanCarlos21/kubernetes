mkdir kube1
cd kube1

##### pods
kubectl run wordpress --image=wordpress --dry-run=client --port=8080 -o yaml > pod_wordpress.yaml
kubectl run mysql --image=mysql:5.7 --dry-run=client  --port=3306 -o yaml > pod_mysql.yaml
"ajouter les variables d'environnements dans les différents pods"
kubectl create -f .

##### services
kubectl expose pod wordpress -o yaml > service_wordpress.yaml
kubectl expose pod mysql -o yaml > service_mysql.yaml

kubectl apply -f .

##### supprimer les services & les pods
kubectl delete pod/mysql 
kubectl delete pod/wordpress
kubectl delete service/wordpress
kubectl delete service/mysql
