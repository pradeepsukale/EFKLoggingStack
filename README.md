# EFKLoggingStack
EFK stack for logging in kubernetes deployment



1. fluentd collects logs from different docker container sources funnels to elasticsearch:

    For this fluentd is suppose to bind to custom role which provides access to docker container logs.
    
2. elasticsearch upong getting data, pushes to kibana for display 
