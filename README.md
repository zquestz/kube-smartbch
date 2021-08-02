# kube-smartbch
Kubernetes configurations for smartBCH on GCE. Note that this requires `cert-manager` if you use the ingress features.

## Deployment
1. Add a new blank disk on GCE called `smartbch-data` that is 20GB. You can always expand it later.
2. Edit `kube/smartbch-ingress.yml` with your preferred domain name.
3. Run `kubectl apply -f kube/smartbch-init-job.yml` to initialize smartBCH.
4. Copy the required dot files onto the volume.
- wget https://github.com/smartbch/artifacts/releases/download/v0.0.3/dot.smartbchd.tgz
- tar zxvf dot.smartbchd.tgz
- cp -rf dot.smartbchd/* /root/.smartbchd/
5. Run `kubectl apply -f kube/smartbch-deployment.yml` to deploy the app.
6. Run `kubectl apply -f kube/smartbch-srv.yml` to setup the kubernetes service.
7. Run `kubectl apply -f kube/smartbch-ingress.yml` to add ingress from outside the cluster.
8. Run `kubectl apply -f kube/smartbch-wss-ingress.yml` to add websocket ingress from outside the cluster.
9. Profit!
