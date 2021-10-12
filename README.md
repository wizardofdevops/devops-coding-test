## DevOps Coding Test:


  
**Problem**: We have a repository with definitions to run containers in docker-compose. We need to run them in kubernetes.

**Goal**:
- create kubernetes manifests to define all the necessary components to run this application in K8S.
	 - "base" folder - should contain minimal amount of k8s manifests to bring it in line with the given docker-compose file.
- Use kustomize to create two overlays
	 - "dev" overlay
	 	 - Use a more recent version of grafana (latest is fine)

	 - "qa" overlay
		 - Use a different influxdb Database username and password Env Variable than the Dev Overlay. Take note of the version of influx --- This is changed in later versions of influx (The docker-compose file given doesn't actually define a default influx user/pass)

- Provide Instructions for deploying your new application to k8s using a readme.md file.

- once done, commit your code to a branch called feature/k8s-manifest and open a pull request to the main branch. Put the manifests in the folder called k8s-manifests
  

**Assumptions**:

- you can use minikube locally to do this project

- all k8s objects should be in the devops-test-{your-first-name} namespace

- ingress objects aren't required

- its OK to submit unecrypted secrets in this instance... but never any other time. :P

