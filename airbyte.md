## Debugging Airbyte deployed by `abctl`

On machine where you have your Airbyte deployed, install [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) and [kubectx + kubens](https://github.com/ahmetb/kubectx) and [k9s](https://k9scli.io/)
then execute commands:

```bash
mkdir -p ~/.kube
KUBECONFIG=~/.airbyte/abctl/abctl.kubeconfig kubectl config view --flatten > ~/.kube/config
kubectx kind-airbyte-abctl
kubens airbyte-abctl
k9s
```

## Debugging Airbyte deployed by `helm` on Kubernetes cluster

On your local machine or any machine that has access to Kubernetes cluster with Airbyte, install [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) and [kubectx + kubens](https://github.com/ahmetb/kubectx) and [k9s](https://k9scli.io/)
then execute commands:

```bash
kubens airbyte # change namespace where your Airbyte is deployed
k9s
```

## Connecting to Airbyte database (Airbyte deployed by `abctl`)

On machine where you have your Airbyte deployed, install [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl) and [kubectx + kubens](https://github.com/ahmetb/kubectx) and [k9s](https://k9scli.io/)
then execute commands:

```bash
mkdir -p ~/.kube
KUBECONFIG=~/.airbyte/abctl/abctl.kubeconfig kubectl config view --flatten > ~/.kube/config
kubectx kind-airbyte-abctl
kubens airbyte-abctl
kubectl port-forward airbyte-db-0 5432:5432
```

Now you can connect to your Airbyte database via `localhost:5432`, e.g. `psql -h localhost -p 5432 -U airbyte -d db-airbyte`
