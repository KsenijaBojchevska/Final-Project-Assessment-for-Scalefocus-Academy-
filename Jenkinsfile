pipeline {
   agent {
        kubernetes {
            label "build-pod"
            cloud "kubernetes"
            yaml '''
apiVersion: v1
kind: Pod
metadata:
  namespace: build-ns
  labels:
    job: bootvar-build-pod
spec:
  containers:
  - name: bootvar-container
    image: alpine:latest
    tty: true
    command: ['cat']
'''
        }
    }
  stages {
    stage('check wp and build') {
      steps {
        script {
            def namespace = false
            if (params.namespace != null){
             namespace = params.namespace
             println "namespace=${namespace}"
             }else{
             println "namespace not found"
             }
       
           }
        
          script {
            def WordPress = false
            if (params.WordPress != null){
             WordPress = params.WordPress
             println "WordPress=${WordPress}"
             }else{
            sh "helm install my-release oci://registry-1.docker.io/bitnamicharts/wordpress"
             }
        
       
        }
      }
    }
  }
  
 /* stage('Deploy') { 
            steps {
                // 
            }
} */
}
