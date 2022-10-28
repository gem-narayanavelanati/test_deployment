node {
	//options {
        // This is required if you want to clean before build
       // skipDefaultCheckout(true)
    //}
	stage('K8s Deploy') {
		kubeconfig(credentialsId: 'KubernetesKubeConfig', serverUrl: 'https://10.50.16.16:6443') {
                              sh'kubectl apply -f Deployment.yml'
                    }
		
		}
	}
	
