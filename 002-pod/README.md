# Part 2 - Understanding pods

In this part we will work on building an understanding on pods trough practice.

## Pods

Pods are the lowest-level primite in kubernetes, it's simply a group of containers that share the same host.
Like every kubernetes resources, Pods can be namespaced. Note that pods are short lived and are not restarted automatically on crash/deletion.

## A simple example

Let's start with a very basic example, run the following command:

    kubectl apply -f simple/pod.yaml

This command will instruct kubernetes to create a pod, take some time to look at the YAML definition
and try to make sense of it.

Now you can run `kubectl get pod` to get the list of running pods in the `default` namespace.

        NAME         READY   STATUS    RESTARTS   AGE
        simple-pod   1/1     Running   0          8m2s

You shoud see the pod we just deployed with the previous command.

## Let's get wild

Kubernetes is full of feature and it would be almost impossible to convey everything during this workshop. For that same reason we decided to 
focus this workshop on teaching how to learn kubernetes by yourself.

Try to achieve the following tasks:

- find the command to **show logs** of the pod you just created
- find the command to **describe** the pod you just created
- find the command to **port forward** trafic from your local machine directly to the pod. You can now visit the content delivered by the container.
- find the command to **delete** the pod you just created


What happened after the last command? Yes the pod disapeared and nothing else happened, this pod is lost forever.

## A lot of parameters

As you can see in the [provided example](simple/pod.yaml) there is a lot of possible options, let's try to understand.

    apiVersion: v1                          # The version we are using for that specific resource
    kind: Pod                               # The type of resources we are deploying
    metadata:
    name: simple-pod                        # The name given to the pod
    labels:
        name: simple-pod                    # Some labels that can be used to search this pod.
    spec:
    containers:                             # List of containers deployed
    - name: simple-pod
        image: jmalloc/echo-server          # Docker image we want to deploy in the first container
        env:                                # The environment passed to the container.
        - name: PORT
          value: "8080"
        resources:                          # Resources allocated to the pod
            limits:
                memory: "128Mi"
                cpu: "500m"
        ports:                              # Ports exposed by the pod. You can optionally give a name to the pod, here 'http'
        - containerPort: 8080
            name: http

You should be up to speed with pods for now, try to remember all the commands you learnt in that part because we will use very similar one 
in the next part when we talk about deployments.