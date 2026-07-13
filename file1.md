History:

		- phase1(2000s)
			- traditional Deployment Era include:
				- on-premises Deployment->each company has it's own data centers.
				- Teams of sysadmins -> these are teams who managed fleets of servers which was(labor intensive+immature process)
				- Bare Metal servers -> applications are run on physical servers.
				- Monolithic Architecture ->  application was built as single units..
				- Homegrown Monitoring tools -> you need   tools to monitors these services..
		- phase2(2010s)
			- know as : Virtualized Deployment Era
				- at these days you could make ;
					- cloud computings -> manage  VMs by  creating +destroying it..
						- this provide flexibility+scalability.
					- Configuration management tools like; Puppt+chef was using to manage those infrastructure.
					- Improved tooling -> as tools improve you can manage large numbers of applications..
		- phase3(2020s)
			- known as: Container Deployment Era.
				- Workload Orchestrations -> Kubernetes treat clusters of machines as a single reesouce + simplify managment+scaling
				- Also these containers (orchestrators) provide interfaces to handle:
					- Efficient scheduling
					- Health checks
					- Service Discovery.
					- Autoscaling ->adjust number of instances based on demand.
					- Persistent storage -> manage storage that persist beyond the lifecycle   of containers.
					- Networking ==>ensuring networking between services.

----
# Structure

  - <img width="1138" height="829" alt="image" src="https://github.com/user-attachments/assets/c5278954-a2a4-48c9-b53d-ddb29e6737c8" />

    -- Node -> server computer inside the  cluster.
    - Control plane -> subset of nodes that are dedicated to perform system tasks.
    	- nodes inside control plane-> control plane nodes.
    - Data Plane -> subset of nodes that are responsible for running user workloads 
    	- nodes inside it called; worker nodes.

- Kubernetes system componants
  - <img width="1106" height="813" alt="image" src="https://github.com/user-attachments/assets/2908562b-d610-416d-803f-ae2dcb68b92f" />

    - etcd -> key-value  store used for storing all the cluster data.
		- kube-apiserver -> frontend of kubernetes control plane.
		- kube-scheduler -> schedule pods into appropriate nodes based on resource availability..
		- kube-controller-manager -> Run controller processes 
			- each controller -> separate process  =>manage routine tasks (maintaining the state of the resources,managing replication,node operations..)
		- Cloud-controller manager -> it interact with cloud provider in order to manage cloud resources (load balancer..)
		- Kubelet -> an agent runs on worker node -> ensure the container is running in pods + manage lifecycle of containers.
		- kube-proxy -> runs on each node  + allow network rules to run into or from pods.
	
		

----

Dependencies  you need to install before working on kubernetes;

		- docker.io...
		- devbox -> in order to make an isolated environment to run your code on top of it.
		- act ->run github actions locally.(important)
		- civo -> CLI to interact with civo cloud.
		- **cloud-provider-kind**: KinD plugin to support LoadBalancer type services
		- **envsubst**: Substitute environment variables into text files
		- **gh**: CLI for managing repositories and interacting with GitHub
		- **go**: Programming language for building scalable and efficient software
		- **task**: Task runner for storing/documenting common commands(important)
		- **google-cloud-sdk (gcloud)**: CLI for managing resources on Google Cloud Platform(or you can use Aws as you want )
		- **gum**: CLI tool for creating interactive and scriptable terminal UIs
		- **helm**: Package manager for Kubernetes(important)
		- **jq**: Command-line JSON processor(good with ips that  outputs from instances (return to workflow in lab7 in mini_labs in Terraform you will understand it ))
		- **k9s**: Terminal UI for managing Kubernetes clusters(important)
		- **kind**: Kubernetes IN Docker - local Kubernetes clusters using Docker container nodes
		- **kluctl**: Deployment tool for Kubernetes(important)
		- **ko**: Build and deploy container images for Go applications
		- **kubectl**: CLI for interacting with Kubernetes clusters(important)
		- **kubectx**: Switch between Kubernetes contexts and namespaces
		- **kubent**: Identify deprecated Kubernetes APIs in a cluster
		- **kustomize**: Customize Kubernetes resource definitions
		- **oras**: OCI Registry As Storage - store artifacts in OCI-compliant registries
		- **nodejs_20**: JavaScript runtime built on Chrome's V8 engine
		- **poetry**: Dependency management and packaging tool for Python(you can use pip)
		- **python312**: Python programming language version 3.12
		- **tilt**: Simplify and accelerate Kubernetes development
		- **yq**: Process YAML documents from the CLI, similar to jq for JSON
