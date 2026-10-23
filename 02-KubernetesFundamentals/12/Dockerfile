
FROM ghcr.io/learnk8s/labs-fundamentals:kubescratch

kubectl run ephemeral-demo --image=ghcr.io/learnk8s/labs-fundamentals:kubescratch --restart=Never

kubectl debug -it ephemeral-demo --image=nilcons/debian --target=ephemeral-demo