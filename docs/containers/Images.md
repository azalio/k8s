https://kubernetes.io/docs/concepts/containers/images/

You create your Docker image and push it to a registry before referring to it in a Kubernetes pod.
* Note that you should avoid using :latest tag, see Best Practices for Configuration for more information
* Docker stores keys for private registries in the $HOME/.dockercfg or $HOME/.docker/config.json file. If you put this in the $HOME of user root on a kubelet, then docker will use it.

https://kubernetes.io/docs/concepts/containers/container-environment-variables/
https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/

There are two hooks that are exposed to Containers:

**PostStart**
* This hook executes immediately after a container is created. However, there is no guarantee that the hook will execute before the container ENTRYPOINT. No parameters are passed to the handler.

**PreStop**
* This hook is called immediately before a container is terminated. It is blocking, meaning it is synchronous, so it must complete before the call to delete the container can be sent. No parameters are passed to the handler.
A more detailed description of the termination behavior can be found in Termination of Pods.

Hook handler calls are synchronous within the context of the Pod containing the Container. 
This means that for a PostStart hook, the Container ENTRYPOINT and hook fire asynchronously. 
However, if the hook takes too long to run or hangs, the Container cannot reach a running state.

The behavior is similar for a PreStop hook. 
If the hook hangs during execution, the Pod phase stays in a running state and never reaches failed. 

If a PostStart or PreStop hook fails, it kills the Container.

Hook delivery is intended to be at least once, which means that a hook may be called multiple times for any given event.

Generally, only single deliveries are made. If, for example, 
an HTTP hook receiver is down and is unable to take traffic, there is no attempt to resend.

Debugging Hook handlers:
* kubectl describe pod <pod_name>

