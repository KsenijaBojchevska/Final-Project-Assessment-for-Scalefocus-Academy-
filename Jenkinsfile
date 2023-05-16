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
      }
    }
  }
}
