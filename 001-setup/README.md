# Part 1 - Setup

Perfect, we are ready to start, the first step is for you to install the following tools

## Kubernetes tools

Kubernetes tools include the command line tool kubectl that can be used to interact with kubernetes, depending on your operating system you will need to follow one of the below guides:

- [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)
- [MacOS](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/)
- [Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/)

After the installation process you can try to run the command

    kubectl get pod

You should see a network error, that's good you're all set.

## Kind     

Kind is a small utility to simulate kubernetes cluster on your own machine essentially allowing you to test before deploying to production and making it a great place for experimentation.

To install kind on **Linux** run:

        curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.11.1/kind-linux-amd64
        chmod +x ./kind
        mv ./kind /some-dir-in-your-PATH/kind

To install kind on **MacOS** run:

        brew install kind

Finally if you are someone on the dark side you can install it on Windows:

        curl.exe -Lo kind-windows-amd64.exe https://kind.sigs.k8s.io/dl/v0.11.1/kind-windows-amd64
        Move-Item .\kind-windows-amd64.exe c:\some-dir-in-your-PATH\kind.exe

You can also install it using [Chocolatey](https://chocolatey.org/packages/kind) if you feel guilty using windows.


After the installation on kind, you can simply run:

        kind create cluster --name covergo-workshop

And at any time you can simply destroy the cluster buy running:

        kind delete cluster --name covergo-workshop


You are now ready to continue to part 2, well done.
