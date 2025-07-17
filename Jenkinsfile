@Library('shared')_
pipeline{
    agent { label "agent"}
    
    
    stages{
        stage ('code'){
            steps{
               sh "echo this is clonning stage"
                script{
                    clone("https://github.com/rahul6364/notesapp-django.git","main")
                }
            }
        }
        stage ('build'){
            steps{
               
                script{
                    build("notes-app","latest")
                }
            }
        }
        stage ('push to dockerhub'){
            steps{
                
                script{
                    docker_push("notes-app","latest")
                }                
            }
        }
        stage ('deploy'){
            steps{
                sh "echo this is deploy step"
                sh "docker compose down ||true "
                sh "docker compose up --build --remove-orphans -d"

            }
        }
        
    }
    
}
