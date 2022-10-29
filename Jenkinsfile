node {
	stage('cloning git repo') {
		cleanWs()
		    dir('DEployment_Test') {
                git branch: 'main', url:'https://github.com/gem-khushiporwal/test_deployment.git'
	        }
	}
	stage('K8s Deploy') {
		dir('DEployment_Test') {
		    kubeconfig(credentialsId: 'KubeConfigCred', serverUrl: 'https://10.50.16.10:8443') {
                sh 'kubectl apply -f Deployment.yml'
            }
		}
		
	}
}
	
