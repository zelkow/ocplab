 __kubeflow on Openshift__


 openshift 4 / ibm cloud


 Architecture of OCP 4 in IBMCLOUD : https://cloud.ibm.com/docs/openshift?topic=openshift-service-arch

 Installation and info regarding KF install on Openshift : https://developers.redhat.com/blog/2020/02/10/installing-kubeflow-v0-7-on-openshift-4-2/


__Prereq__

 i use existing cluster from IRBLAB
 install ibm CLI and latest OC client
 checking login to oc

__Installation of Kubeflow__

 Kubeflow 1.0 on Openshift 4.4.17

 Installing kfctl 1.1 from latest release : https://github.com/kubeflow/kfctl/releases/tag/v1.1.0

 Understanding the kfctl and kubeflow configuration process : https://www.kubeflow.org/docs/ibm/deploy/install-kubeflow/
 
 
  - getting the standard config yaml file (kustumize targets, overlays)
  - select type of install (istio, kubernetes, openshift)
  - configure locally in kubeflow_config
  - apply to the (oc/k8) cluster


		git clone https://github.com/opendatahub-io/manifests.git
		cd manifests
 		sed -i 's#uri: .*#uri: '$PWD'#' ./kfdef/kfctl_openshift.yaml
		kfctl build --file=kfdef/kfctl_openshift.yaml
		kfctl apply --file=./kfdef/kfctl_openshift.yaml

 - checks 
 
 		oc get pods
 		