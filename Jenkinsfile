  pipeline {
    agent any
    tools {
        terraform 'Terraform14'

    }
    stages { 
        stage('kubectl yaml') {
        steps {
          withCredentials([file(credentialsId: 'gk_test3', variable: 'GC_KEY')]) {
            sh 'gcloud auth activate-service-account --key-file=${GC_KEY}'
            sh ("gcloud container clusters get-credentials copper-creek-334508-gke --region asia-northeast1 --project copper-creek-334508")
            sh ("/usr/local/bin/kubectl apply -f rbac.yaml")
            sh ("/usr/local/bin/kubectl apply -f elk.yaml")
            sh ("/usr/local/bin/kubectl apply -f elk-service.yaml")
            sh ("/usr/local/bin/kubectl apply -f logstash-config.yaml")
            sh ("/usr/local/bin/kubectl apply -f logstash-deployment.yaml")
            sh ("/usr/local/bin/kubectl apply -f logstash-service.yaml")
            sh ("/usr/local/bin/kubectl apply -f filebeat.yaml")
            sh ("/usr/local/bin/kubectl apply -f kibana.yaml")
            sh ("/usr/local/bin/kubectl apply -f nginx.yaml")
            sh ("/usr/local/bin/kubectl apply -f nginx-service.yaml")
            sh ("/usr/local/bin/kubectl apply -f index-html-configmap.yaml")
            sh ("/usr/local/bin/kubectl rollout restart deployment nginx-deployment")

            
                 }
          

          
        }
      } 

    }
     
  }
