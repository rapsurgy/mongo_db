pipeline{
    agent any
    stages{
        stage("Git checkout"){
            steps{
                 git branch: 'main', url: 'https://github.com/rapsurgy/mongo_db'
            }
        }
        stage("deploy to AKS"){
            steps{
                script{
                    kubernetesDeploy(
                        configs: "mongodb-secret.yaml",
                        kubeconfigid: 'K8S',    
                        enableConfigSubstitution: false
                        )
                    kubernetesDeploy(
                        configs: "configmap.yaml",
                        kubeconfigid: 'K8S',    
                        enableConfigSubstitution: false         
                        )
                    kubernetesDeploy(
                        configs: "mongo.yaml",
                        kubeconfigid: 'K8S',    
                        enableConfigSubstitution: false         
                        )
                    kubernetesDeploy(
                        configs: "mongoexpress.yaml",
                        kubeconfigid: 'K8S',    
                        enableConfigSubstitution: false         
                        )            
                }
            }
        }   
    
        
    }
}