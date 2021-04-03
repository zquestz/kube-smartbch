# kube-smartbch
Kubernetes configurations for smartBCH on GCE. Note that this requires `cert-manager` if you use the ingress features.

## Deployment
1. Add a new blank disk on GCE called `smartbch-data` that is 20GB. You can always expand it later.
2. Edit `kube/smartbch-ingress.yml` with your preferred domain name.
3. Edit `kube/smartbch-init-job.yml` with your keys.
4. Run `kubectl apply -f kube/smartbch-init-job.yml` to initialize smartBCH with your keys.
5. Run `kubectl apply -f kube/smartbch-deployment.yml` to deploy the app.
6. Run `kubectl apply -f kube/smartbch-srv.yml` to setup the kubernetes service.
7. Run `kubectl apply -f kube/smartbch-ingress.yml` to add ingress from outside the cluster.
8. Profit!
