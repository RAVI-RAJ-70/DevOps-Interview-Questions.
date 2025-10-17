📌 Containers (Docker & Kubernetes) – 100+ Interview Questions

🚀 Beginner-Level Docker & Kubernetes Questions (1–20)

🚀 Intermediate-Level Docker & Kubernetes Questions (21–40)

🚀 Advanced-Level Docker & Kubernetes Questions (41–60)

🧠 Scenario-Based & Practical Questions (61–80)
61. How do you access a running container to debug an issue?

Answer:

Use docker exec:

docker exec -it my-container /bin/bash


-it: Interactive terminal

/bin/bash or /bin/sh: Access shell inside container

62. What will you do if a Kubernetes pod is stuck in CrashLoopBackOff?

Answer:

Check logs:

kubectl logs pod-name


Describe the pod:

kubectl describe pod pod-name


Enter the container:

kubectl exec -it pod-name -- /bin/sh

63. A Docker container exits immediately after starting. How do you troubleshoot it?

Answer:

Check logs:

docker logs container-id


Use docker run interactively to test:

docker run -it image-name /bin/bash

64. How do you share logs from a running container with a team member?

Answer:

Save logs to a file:

docker logs container-name > logs.txt


Share via version control or secure file transfer.

65. How do you handle a service crash inside Kubernetes without affecting other services?

Answer:

Kubernetes isolates services using Pods and Deployments:

Restart only the affected pod:

kubectl delete pod pod-name


Other services remain unaffected due to isolation.

66. How to find which container is using the most resources in Kubernetes?

Answer:

Use kubectl top (with Metrics Server installed):

kubectl top pod
kubectl top node

67. How do you simulate high traffic for load testing in Kubernetes?

Answer:

Use tools like:

ab (Apache Bench)

wrk

k6

Run from inside a container:

kubectl run -i --tty load-tester --image=busybox --restart=Never -- sh

68. How do you find which image version a pod is using?

Answer:

kubectl get pod pod-name -o jsonpath='{.spec.containers[*].image}'

69. What happens when you update a ConfigMap used by a running pod?

Answer:

The pod does not automatically reload the new config.

You must recreate the pod or use a reloader sidecar tool.

70. How do you make a Kubernetes pod restart every day automatically?

Answer:

Use a CronJob to delete the pod or use a restart trigger via annotation.

71. How do you roll back a failed deployment in Kubernetes?

Answer:

kubectl rollout undo deployment/my-deployment

72. How do you validate a Kubernetes YAML file before applying it?

Answer:

kubectl apply --dry-run=client -f myfile.yaml

73. What is the fastest way to test a one-time command inside a Docker container?

Answer:

docker run --rm alpine echo "Hello"


--rm: Removes container after exit

74. What do you do when a container needs access to a host port <1024 without root?

Answer:

Use port forwarding via NGINX or iptables

OR run container in privileged mode (not recommended for production)

75. How do you monitor a specific container’s real-time logs in Kubernetes?

Answer:

kubectl logs -f pod-name container-name

76. A pod is stuck in Pending state. What could be the reasons?

Answer:

Not enough resources (CPU/Memory)

Missing node affinity

PVC not available

Taints preventing scheduling

77. How do you execute a command inside an already running Kubernetes pod?

Answer:

kubectl exec -it pod-name -- /bin/sh

78. How to expose a Docker container on port 8080 of the host machine?

Answer:

docker run -p 8080:80 nginx

79. How do you check if a Kubernetes Deployment is fully rolled out?

Answer:

kubectl rollout status deployment my-deployment

80. How do you run a container only during build and not include it in production?

Answer:

Use multi-stage builds and copy only the final artifact.

🔧 Container Creation & Command-Focused Questions (81–100)
81. How many ways can you create a Docker container?

Answer:

Using image:

docker run nginx


From Dockerfile:

docker build -t myapp .
docker run myapp


Using Docker Compose:

docker-compose up


Kubernetes Pod YAML:

kubectl apply -f pod.yaml


Kubernetes Deployment:

kubectl create deployment myapp --image=nginx

82. How do you create and name a container using Docker CLI?

Answer:

docker run --name my-container nginx

83. How do you start a container in interactive mode?

Answer:

docker run -it ubuntu /bin/bash

84. How do you run a container in the background?

Answer:

docker run -d nginx

85. How do you assign a container to a specific network?

Answer:

docker network create mynet
docker run --network=mynet nginx

86. How do you build a Docker image with a tag?

Answer:

docker build -t myapp:v1 .

87. How do you commit changes from a running container to a new image?

Answer:

docker commit container-id mynewimage

88. How do you restart a stopped container?

Answer:

docker start container-name

89. How do you list all images and containers?

Answer:

docker images
docker ps -a

90. How do you remove all stopped containers?

Answer:

docker container prune

91. How do you map host volume to container?

Answer:

docker run -v /host/path:/container/path nginx

92. How do you get into a running container?

Answer:

docker exec -it container-name /bin/bash

93. How do you find the IP of a Docker container?

Answer:

docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container-name

94. How do you restart a Kubernetes deployment?

Answer:

kubectl rollout restart deployment my-deployment

95. How do you create a Kubernetes pod using imperative command?

Answer:

kubectl run mypod --image=nginx

96. How do you delete all containers and images in Docker?

Answer:

docker rm -f $(docker ps -aq)
docker rmi -f $(docker images -q)

97. How do you expose a Kubernetes deployment as a service?

Answer:

kubectl expose deployment myapp --port=80 --type=NodePort

98. How do you edit a running deployment?

Answer:

kubectl edit deployment
