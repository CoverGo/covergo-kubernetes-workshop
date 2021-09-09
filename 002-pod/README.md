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
- find the command to **delete** the pod you just created


What happened after the last command? Yes the pod disapeared and nothing else happened, this pod is lost forever.