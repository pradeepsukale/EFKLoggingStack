# EFKLoggingStack
EFK stack for logging in kubernetes deployment



1. fluentd collects logs from different docker container sources funnels to elasticsearch:

    For this fluentd is suppose to bind to custom role which provides access to docker container logs.
    
2. elasticsearch upong getting data, pushes to kibana for display 


fluentd-rbac.yaml - Creates 'ServiceAccount' with 'ClusterRole' to get access to docker logs. Also, once this role is created, it binds the pod to this ClusterRule.
