To bootstrap a cluster with these manifests, do the following:

Run the commands:
1. helm dependency update charts/argo-cd/
2. helm install argo-cd charts/argo-cd/ -n argocd --create-namespace
3. helm template charts/root-app/ | kubectl apply -f -

Now you can access the Argo-CD webpage by doing the following:
1. kubectl port-forward svc/argo-cd-argocd-server 8080:443 -n argocd
2. Use the username "admin", and the password retrieved by this command: kubectl get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" -n argocd | base64 -d

There you go! Now you have a Argo-CD git-ops cluster bootstrapped and ready to go!