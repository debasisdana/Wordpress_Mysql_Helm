# Wordpress_Mysql_Helm


this is for deployment of Wordpress and Mysql with help of Helmchart
---------------------Instruction-------

----Install Helm----
curl -L https://git.io/get_helm.sh | bash -s -- --version v3.8.2
chmod 600 /var/lib/jenkins/.kube/config
helm repo add stable https://charts.helm.sh/stable
helm search repo stable
--------Deploying Wordpress----
cd <root_dir>
git clone <this repository>
cd wpws
-bash-4.2$ helm install wpws wpws
[root@ip-172-31-237-7 ~]# kubectl get po
NAME                             READY   STATUS    RESTARTS   AGE
wordpress-7d6b68bdf8-x2zn4       1/1     Running   0          22s

[root@ip-172-31-237-7 ~]#
[root@ip-172-31-237-7 ~]# kubectl get svc

NAME            TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE

kubernetes      ClusterIP   10.100.0.1       <none>        443/TCP        3h52m

wordpress       NodePort    10.100.191.181   <none>        80:32323/TCP   41s

[root@ip-172-31-237-7 ~]#


access below UTL:

http://<node1_ip>:<nodeport>

http://<node2_ip>:<nodeport>

example: http://3.136.236.158:32323/


--------Deploying Myql----
cd dbws

-bash-4.2$ helm install dbws dbws

-bash-4.2$ helm list

NAME            NAMESPACE       REVISION        UPDATED                                 STATUS          CHART           APP VERSION

dbws            default         1               2022-12-10 12:01:48.034338856 +0000 UTC deployed        dbws-0.1        0.1

wpws            default         1               2022-12-10 10:52:20.968687364 +0000 UTC deployed        wpws-0.1        0.1

[root@ip-172-31-237-7 ~]# kubectl get po

NAME                             READY   STATUS    RESTARTS   AGE

mysql-78dd647967-4rhn8           1/1     Running   0          20s

wordpress-7d6b68bdf8-x2zn4       1/1     Running   0          69m

------Configure wordpress----

1. access below Wordpress url

http://<node1_ip>:<nodeport>

input for mysql in Wordpress-->dbws\templates\mysql.yml




