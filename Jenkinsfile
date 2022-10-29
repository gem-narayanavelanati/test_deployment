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
			    """
    cat <<EOF >> Deployment.yml
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: nginx
    spec:
      selector:
        matchLabels:
          app: nginx
      strategy:
        type: Recreate
      template:
        metadata:
          labels:
            app: nginx
        spec:
          containers:
          - image: nginx:latest
            name: nginx
            ports:
            - containerPort: 80
              name: web
    EOF
"""
			    sh 'kubectl version'
                            sh 'kubectl apply -f Deployment.yml'
                    }
		}
		
	}
}
	
