# Part 4 - Service

You may have asked yourself the question, how can I access my deployment? So far we have only been using
the port-forwarding option but it's not managing load balacing for us and it's definitely not production ready.

This is when services are useful, a service is like an internal load balancer fully managed by kubernetes.

# Multiple type of services

With almost all type of kubernetes services, kubernetes is using an internal load balancer but it's possible 
to expose this load balancer publicly or within the cluster. Here are the main service types:

- ClusterIP: Exposes a service which is only accessible from within the cluster.
- NodePort: Exposes a service via a static port on each node's IP.
- LoadBalancer: Exposes the service via the cloud provider's load balancer.

# Simple service

The simple deployment from the last part should still be running inside your cluster with 2 replicas. Let's try to create
a service of type ClusterIP to load balance trafic between the 2 replicas.

Run the command:

    kubectl apply -f manifest/service_cluster.yaml

Since this service type is ClusterIP, it's only reachable from within the cluster so you will need to run the port forward command you learnt previously but this time you need to target a service and not a pod.

# How?

This is probably what you are asking yourself now "how did my service found the deployment I deployed before". Take a look and try to
figure out from the [manifest file](manifest/service_cluster.yaml). 

Hint: Think about labels we defined before.

# Exposing publicly

When using kubernetes in a cloud provider, Kubernetes will by automatically configured to create a cloud load balancer when using the service type **Load Balancer**. This cloud load balancer redirect the trafic to the internal load balancer of kubernetes.

You laptop not being a cloud provider this is complicated to demonstrate, look at the demo.
