make sure before you start ; clone that project :https://github.com/sidpalas/devops-directive-kubernetes-course
in order to apply all the concepts.
# Local KinD cluster
  - KinD -> Kubernetes in Docker -> local kubernetes on your machine this is good for testing..
  - KinD -> allows multi node clusters => simulates having separate control plane+worker nodes.

How to go through it?

         - before generting the cluster -> build kind-config.yml file(in order to define local paths for persistent volumes(PV)
            REPLACE_WITH_ABSOLUTE_PATH=${PWD} envsubst < kind-config.yaml.TEMPLATE > kind-config.yaml
              -as you see we read the data from template and substitute my actual data in it then we plant it inside kind-config.yaml (because KinD will use it to make PV)
- now create the cluster:

```bash
kind create cluster --config kind-config.yaml
```

Break it into 4 parts:

```text
kind | create | cluster | --config kind-config.yaml
```

## 1. `kind`

`kind` means **Kubernetes IN Docker**.

It is the CLI program you're executing.

Same idea as:

```bash
docker ...
terraform ...
kubectl ...
kind ...
```

## 2. `create`

The action you want KinD to perform:

```bash
kind create
```

You're saying:

> KinD, create something.

## 3. `cluster`

What do you want to create?

```bash
kind create cluster
```

> KinD, create a Kubernetes cluster.

Without a custom config, you can simply run:

```bash
kind create cluster
```

That creates a basic local cluster.

## 4. `--config kind-config.yaml`

This tells KinD:

> When creating the cluster, use the settings from `kind-config.yaml`.

```text
kind
 │
 ▼
reads kind-config.yaml
 │
 ▼
understands desired nodes/mounts/settings
 │
 ▼
creates Docker containers
 │
 ▼
bootstraps Kubernetes inside them
```

For example, if the config says:

```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4

nodes:
  - role: control-plane
  - role: worker
  - role: worker
```

KinD understands:

```text
I need 3 Kubernetes nodes

1 control plane
2 workers
```

Then you'll probably see something like this in Docker:

```bash
docker ps
```

```text
kind-control-plane
kind-worker
kind-worker2
```

Each **Kubernetes node is a Docker container**.

## What actually happens when you run the command?

Conceptually:

```text
$ kind create cluster --config kind-config.yaml
                    │
                    ▼
          Read configuration
                    │
                    ▼
        Create Docker network
                    │
                    ▼
      Create node containers
                    │
          ┌─────────┴─────────┐
          ▼                   ▼
  control-plane            workers
          │                   │
          └─────────┬─────────┘
                    ▼
       Bootstrap Kubernetes
                    │
                    ▼
          Generate kubeconfig
                    │
                    ▼
       kubectl can access cluster
```

Afterward, run:

```bash
docker ps
```

You see the **containers/nodes**.

Then:

```bash
kubectl get nodes
```

You see the same machines from the **Kubernetes perspective**.

That's a very important distinction:

```text
docker ps
→ Docker's view

kubectl get nodes
→ Kubernetes' view
```


