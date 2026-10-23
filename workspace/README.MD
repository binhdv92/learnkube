[LearnKube] Amin Astaneh  [9:41 AM]
Getting started with Docker - https://academy.learnk8s.io/containers-3 :walking:
Creating Images - https://academy.learnk8s.io/containers-4 :camera:
Managing State - https://academy.learnk8s.io/containers-5 :floppy_disk:
Networking - https://academy.learnk8s.io/containers-6 :electric_plug:
Packaging an app - https://academy.learnk8s.io/containers-7 :package:
Debugging - https://academy.learnk8s.io/containers-8 :bug:
Challenges - https://academy.learnk8s.io/container-challenges-intro :lock: (edited)

Homework:
# https://academy.learnk8s.io/containers
1. 
    docker run  -ti --rm -e VERSION=13 -v "./data:/data" ghcr.io/learnk8s/labs-docker:details bash
    docker image inspect ghcr.io/learnk8s/labs-docker:details

## Building walls
ghcr.io/learnk8s/labs-docker:walls
docker run -d ghcr.io/learnk8s/labs-docker:walls
docker run -ti ghcr.io/learnk8s/labs-docker:walls bash
docker image inspect ghcr.io/learnk8s/labs-docker:walls

docker exec -it ab98a78ba884 bash 



# Section 2
https://academy.learnk8s.io/fundamentals-first-deployment

Your VM is ready, open vanbinh.workspace.learnkube.com (20.127.137.177) in Google Chrome, password is: broad-base, SSH with the same password: ubuntu@20.127.137.177



kubectl run podinfo --image=ghcr.io/stefanprodan/podinfo:6.2.2

