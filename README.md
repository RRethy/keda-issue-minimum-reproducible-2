To reproduce the issue, run the following:

```bash
# creates a kind cluster with a ScaledObject and Deployment
./setup.sh

# Run these in 3 different terminals
kubectl --context kind-kind --namespace foobar get hpa -w
kubectl --context kind-kind --namespace foobar get deployment -w
kubectl --context kind-kind --namespace foobar get scaledobject -w
```

The `Fallback` field in the `-owide` for ScaledObject will switch between `true` and `false` repeatedly.
The replica count for the deployment will go back and forth between 3 and 12 repeatedly.
