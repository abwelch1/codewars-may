# CodeWar Challenges
**VM Login Command**: ```ssh -i <private-key-file> admin@<vm-ip>```  
EX: ssh -i team-1 admin@35.222.181.98

## Word Search Puzzle 

Instructions: Follow this link to access the wordsearch challenge https://thewordsearch.com/puzzle/2267121/code-wars-70-word-search/ and select "begin".
How to verify/submit: Screenshot your completed word search puzzle and send the picture in your team’s breakout room chat letting us know that you have completed it.
Potential points: 10 points for fully completing the word search puzzle. 

## Neuralink Trivia Quiz 

Instructions: Follow this link to access the trivia quiz https://forms.gle/nEF1iZacaBPqLHUe8 
How to verify/submit: Notify us in your team’s breakout room chat that you have completed the trivia quiz. Screenshot of the completed quiz is optional. 
Potential points: Each question is worth 1 point. There are a total of 10 questions. 

## Leet Code Challenge 1

Below is a coding challenge on Leet Code. For a correct submission please screenshot of the solution page in your team chat with the challenge number. 
Potential Points: 10 for completion 5 bonus for Golang
https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/

## Leet Code Challenge 2

Below is a coding challenge on Leet Code. For a correct submission please screenshot of the solution page in your team chat with the challenge number. 
Potential Points: 10 for completion 5 bonus for Golang
https://leetcode.com/problems/shuffle-the-array/

## Go Environment Flag
Worth 5 points 

Your VM contains a hidden environment_flag directory. Within that directory is a single Go executable. The executable accepts an argument for the name of an environment variable on your VM, and then attempts to locate that environment variable. If the supplied environment variable name is successfully retrieved, the flag is outputted.

Your task is to run the executable and pass a valid environment variable name. You can use an existing environment variable or create your own. 

HINTS: 
* You don't need to travel far to locate the hidden directory


## Kubernetes/API Flag
Each phase is worth 10 points.

IMPORTANT TIP:
This challenge will require editing numerous files that exist on your team's linux VM. It is recommended that you use one of the supplied command-line editors: nano or vim.

Basic operations with nano:
* open an existing file/create new file with supplied name: ```nano <filename>```
* save file: ```CTRL + O```
* exit file: ```CTRL + X```

### Phase 1:

Your VM contains: docker, a docker image named gates-of-moria, minikube, kubernetes object descriptor files, and the scraps of a Go file that was used to build the docker image.

Your objective for phase one is to complete the kubernetes files, based on the information you review from the Go scraps file. Once you have altered the scripts, you will deploy the objects to the minikube cluster.

HINTS:
* **You only need to replace values that contain ???** (i.e. secret.yaml is already complete)
* All necessary files are located within the ```kubernetes_flag``` directory, located in admin home directory (/home/admin/kubernetes_flag)
* You will need to start minikube ```minikube start```
* You will need to utilize the minikube docker daemon ```eval $(minikube docker-env)```
	* You can now verify that the prebuilt image exists with ```docker images``` (you only need to focus on the gates-of-moria entry)
* scraps.go will not compile in current state but contains all information you need to properly configure the kubernetes files. **You do not need to fix scraps.go. Do not build a new docker image**
* The order that you apply the objects in matters. Review each object descriptor carefully to see if they reference other objects

HELPFUL COMMANDS:
* output file content to terminal: ```cat <filename>```
* deploy an object to the cluster via descriptor file: ```kubectl apply -f <filename>``` EX: ```kubectl apply -f pod.yaml```
* delete an object from the cluster (in case you deploy an object w/ errors): ```kubectl delete -f <filename```
* retrieve basic info about deployed object type: ```kubectl get <object type>``` Example object types: pods, services, secrets
* retrieve logs for pod: ```kubectl logs <pod name>```

HOW TO SUBMIT FOR POINTS:
* Take a screenshot of the output from ```kubectl get pods```. If the status is "Running", you receive points.

### Phase 2:
Congrats on successfully deploying the pod! 

You are likely already aware of this after reviewing scraps.go, but the pod you deployed is running a simple RESTful API.

Your objective for phase two is to configure and execute the proper request to retrieve the flag response from the api.

HINTS:
* You likely noticed the file curl_command.sh. This file outlines the basic structure of the request. Your task is to supply the correct values for each occurence of ???
* The port you specified in service.yaml of Phase 1 is being mapped to a NodePort. **Use the NodePort when building the request**
* Review scraps.go!
* base64 decode the value you send in the request

HELPFUL COMMANDS:
* execute curl_command.sh: ```./curl_command.sh```
* IP of minikube cluster: ```minikube ip```
* retrieve more info on a service object: ```kubectl describe service <service name>```

HOW TO SUBMIT FOR POINTS:
* Paste the flag output into **your team's breakout room chat**


## Nmap/Frontend Flag
Each phase is worth 10 points. 

### Phase 1:
The network that your team VMs are within also contains a VM that is hosting a very popular (and secure!) banking service. 

Your objective for phase one is to access that banking service website.

HINTS:
* your VMs come with nmap pre-installed
* the command ```ip a``` will output network interface information for your VM
	* multiple interface entries exist, be sure to scan the correct interface (or try them all :D)
* use the following subnet mask in cidr notation for your scan: 255.255.255.0
* disregard output for other team VMs
* **the external IP of the banking service VM is appended to the VM's name. Replace the dashes with periods to have a valid ip address**

HOW TO SUBMIT FOR POINTS: 
* Take a screenshot of the banking website homepage and copy/paste it into **your team's breakout room chat**

### Phase 2:
Congrats on gaining access to a very exclusive and innovative banking service. 

Your objective for phase two is to retrieve the flag from the website!

HINTS:
* take some time to fully *inspect* the website (wink, wink)
* two options exist on the site. Both provide further hints to find the flag
* the console tab in your browser will be useful

HOW TO SUBMIT FOR POINTS:
* Paste the flag output into **your team's breakout room chat**
