@Library("Shared") _
pipeline{
    
    agent {label "vinod"}
    stages{
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
              script{
                clone("https://github.com/RITIKRAAJ/django-notes-app.git","main")
              }
            }
        }
        stage("Build"){
            steps{
                script{
                docker_build("notes-app","latest","rithikraj01")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
               script{
                   docker_push("notes-app","latest","rithikraj01")
               }
            }
         }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose up -d"
            }
        }
    }
}
