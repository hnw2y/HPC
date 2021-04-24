# HPC
HPC Dockerfile and .yaml files for cloud computing research project

START UP PROCESS:

	minikube start
	kubectl apply -f nfs-server.yaml
		check IP (using *kubectl describe pod nfs-server*) of container and 
		put it in nfs-volumes.yaml	
	kubectl apply -f nfs-volumes.yaml
	kubectl apply -f user-pod.yaml
	kubectl get pods
	kubectl exec -it nfs-client-xxxxx -- /bin/bash
	as root in the home directory, run these commands (if pv is new):
		mkdir jovyan
		chown -R jovyan:jovyan jovyan
	in all the pods as root:
		service ssh start
	run ssh-keygen as jovyan in /home/jovyan/.ssh directory
	copy id_rsa.pub to authorized_keys
	ssh between all the pods to to add them to known hosts
	
To build the singularity cntainers: 
	
	singularity build mpitest.sif mpitest.def
	singularity build gromacs.sif gromacs.def

To switch to jovyan user: 
	
	su joyvan
	/bin/bash
