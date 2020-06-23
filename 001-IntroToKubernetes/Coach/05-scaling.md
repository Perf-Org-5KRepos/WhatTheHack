# Challenge 5: Coach's Guide

[< Previous Challenge](./04-k8sdeployment.md) - **[Home](../readme.md)** - [Next Challenge >](./06-deploymongo.md)

## Notes & Guidance

- In the YAML file, they will have to update the **spec.replicas** value. They can use this command to edit the deployment resource:
	- `kubectl edit deployment content-web`
- They can watch cluster events by using the following command:
	- `kubectl get events --sort-by='{.lastTimestamp}' --watch`
- The error they will encounter is that there aren’t enough CPUs in the cluster to support the number of replicas they want to scale to.
- The three fixes to address resource constraints are:
	- Use the Azure portal or CLI to add more nodes to the AKS cluster.
	- Use the cluster autoscaler to automatically add more nodes to the cluster as resources are needed.
	- Change the deployment and reduce the needed CPU number from “0.5” to “0.125” (500m to 125m).
		- This is the preferred solution as long as the application remains responsive!
- **NOTE:** In case they do **NOT** get an error and are able to scale up, check how many nodes they have in their cluster and the size of the node VMs. Over provisioned clusters will not fail.
	- If a team doesn’t get a failure, just have them double the number of Web and API app instances.  
