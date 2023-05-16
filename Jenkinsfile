pipeline {
  agent any
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
}
