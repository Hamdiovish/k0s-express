# Setup cluster:

1. Run k0s:

> docker-compose up -d

2. Log k0s:

> docker logs -f k0s

3. Enter inside k0s:

> docker exec -it k0s bash

4. Check cluster is ready:

> kubectl get nodes:

5. Export kube.config [just wait for few minutes for k0s to be ready]:

> docker exec k0s cat /var/lib/k0s/pki/admin.conf > infra/k0s.config

> export KUBECONFIG=$(pwd)/infra/k0s.config

# Interract with Cluster:

1. Run a sample pod and service:

> kubectl apply -k setup/sample

> kubectl --kubeconfig=infra/k0s.config apply -k setup/sample

2. Reset K0s:

> sudo docker rm -f k0s

3. Reset All:

> docker-compose down -v
