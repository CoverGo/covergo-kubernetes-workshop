# Part 5 - Freestyle

It's time to put your skills to practice and deploy a fully fledged application by yourself.


# PodInfo application

[PodInfo](https://github.com/stefanprodan/podinfo) is an app heavily used to test load balancing and other kind of stuff on kubernetes.

PodInfo is made of a **frontend** and a **backend** service, you are tasked to deploy PodInfo with High avalability (multiple replicas).

Both frontend and backend use the same docker image, you just need to change the command flags passed to the container.


For the frontend app here is the command used to start:

        command:
        - ./podinfo
        - --port=9898
        - --port-metrics=9797
        - --level=info
        - --backend-url=http://backend:9898/echo

And the one for backend:

        command:
        - ./podinfo
        - --port=9898
        - --port-metrics=9797
        - --grpc-port=9999
        - --grpc-service-name=backend
        - --level=info

Look at the diffents informations provided in those different flags and try to figure out
which environment varibles you should provide to each of the container.