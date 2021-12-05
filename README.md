# EFKLoggingStack
EFK stack for logging in kubernetes deployment



1. fluentd collects logs from different docker container sources funnels to elasticsearch:

    For this fluentd is suppose to bind to custom role which provides access to docker container logs.
    
2. elasticsearch upong getting data, pushes to kibana for display 


fluentd-rbac.yaml - Creates 'ServiceAccount' with 'ClusterRole' to get access to docker logs. Also, once this role is created, it binds the pod to this ClusterRule.

From fluentd-daemonset_std.yaml:

      containers:
      - name: fluentd
        image: fluent/fluentd-kubernetes-daemonset:v1-debian-elasticsearch
        env:                                  ----> All these env variables are needed to connect to elasticsearch
          - name:  FLUENT_ELASTICSEARCH_HOST  
            value: "elasticsearch.logging"    ---> here 'logging' is namespace where elasticsearch is created.
          - name:  FLUENT_ELASTICSEARCH_PORT
            value: "9200"

