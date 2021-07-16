# gsc_k8s_graylog

1. Clone git clone https://github.com/stahh/gsc_k8s_graylog.git

2. Go to source directory: cd gsc_k8s_graylog

3. Create a graylog cluster

4. Get cluster name: kubectl config get-contexts

5. Switch to graylog cluster: kubectl config use-context gke_cience-core_us-central1-c_graylog-cluster

6. Create deployments:
 :code: kubectl create -f mongo-deployment.yaml,elasticsearch-service.yaml,graylog-service.yaml
   
7. Check services and get EXTERNAL-IP: kubectl get services

8. Go to Kubernetes Engine -> Workloads -> graylog-deploy and push Edit. In the opened yaml file find line 
value: http://EXTERNAL-IP:9000/ and replace EXTERNAL-IP with real IP address from previous step
   
9. Run in terminal: echo -n "Enter Password: " && head -1 </dev/stdin | tr -d '\n' | sha256sum | cut -d" " -f1 
and put your password. Copy resulting hash, find in yaml file line value: 8c6976e5b5410415bde908bd4dee15dfb167a9c873fc4bb8a81f6f2ab448a918 and replace with copied hash
   
10. Save deployment, wait some time and connect to http://REAL EXTERNAL-IP:9000/