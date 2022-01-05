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
                        configs: "configmap.yaml",
                        configs: "mongo.yaml",
                        configs: "mongoexpress.yaml",
                        kubeconfigid: 'K8S',    
                        enableConfigSubstitution: true         
                        )
                }
            }
        }   
    
        
    }
}