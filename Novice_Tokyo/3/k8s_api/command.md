```
TOKEN=$(cat /var/run/secrets/kubernetes.io/serviceaccount/token)
CACERT=/var/run/secrets/kubernetes.io/serviceaccount/ca.crt
NAMESPACE=$(cat /var/run/secrets/kubernetes.io/serviceaccount/namespace)
k8s=$KUBERNETES_PORT_443_TCP_ADDR:$KUBERNETES_PORT_443_TCP_PORT





curl -X POST -H "Authorization:Bearer $TOKEN" \
--cacert $CACERT -H 'Content-Type:application/json' \
-d @deployment.json https://$k8s/apis/apps/v1/namespaces/apitest/deployments



# curl -X GET -H "Authorization:Bearer $TOKEN" \
--cacert $CACERT \
https://$k8s/apis/apps/v1/namespaces/apitest/deployments/apitest-nginx



# curl -X DELETE -H "Authorization:Bearer $TOKEN" \
--cacert $CACERT \
https://$k8s/apis/apps/v1/namespaces/apitest/deployments/apitest-nginx
```
