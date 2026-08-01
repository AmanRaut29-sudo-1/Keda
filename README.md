What is KEDA?

KEDA is a tool that helps Kubernetes scale applications based on real-world events. With KEDA, we can adjust the size of our containers automatically, depending on the workload—like the number of messages in a queue or incoming requests.

It’s lightweight and works alongside Kubernetes components like the Horizontal Pod Autoscaler (HPA) , It doesn’t replace anything but adds more functionality. we can choose which apps to scale with KEDA while leaving others untouched.

How KEDA works !

KEDA monitors external event sources, like message queues, databases, or APIs, and automatically adjusts the number of running pods based on real-time demand. When events arrive, KEDA scales our workload up to handle the load. When things go quiet, it scales back down, all the way to zero if needed.

It does this by working alongside Kubernetes’ existing Horizontal Pod Autoscaler rather than replacing it. KEDA feeds the HPA with external metrics, extending it beyond CPU and memory to any event source we can connect to. The result is an application that responds to actual workload rather than just infrastructure signals.

For batch workloads, KEDA takes a different approach: instead of scaling a running deployment up or down, it creates new Kubernetes Jobs in response to events, for example, one job per message in a queue.

<img width="1470" height="1280" alt="image" src="https://github.com/user-attachments/assets/f93209d7-4738-42d1-ad12-2989454a80ac" />

KEDA runs three components inside the Kubernetes cluster, each with a distinct responsibility:-
-> keda-operator :-
-> keda-metrics-apiserver
-> keda-admission-webhooks

KEDA uses Custom Resource Definitions (CRDs) to manage scaling behaviour :- 
-> ScaledObject
-> ScaledJob
-> TriggerAuthentication
