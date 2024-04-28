# Using Longhorn with EKS

### Deploy Longhorn via Helm

```sh
### 1. First, add the Longhorn Helm repository:
helm repo add longhorn https://charts.longhorn.io
helm repo update

### 2. Install 
### Install the OS package on the node, this DaemonSet will have privileged access rights.
kubectl apply -f iscsi-dependency.yaml

### 3. Next, install Longhorn with Helm:
helm install longhorn longhorn/longhorn --namespace longhorn-system --create-namespace

### 4. Verify the Installation
### Check the deployment status. All Longhorn components should be running:
kubectl -n longhorn-system get pod

### 5. Checkin the storage class 
kubectl get sc