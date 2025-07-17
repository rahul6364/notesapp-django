@Library('shared')_
pipeline{
    agent { label "agent"}
    
    
    stages{
        stage ('code'){
            steps{
                // sh "echo this is code step"
                // git url: "https://github.com/rahul6364/notesapp-django.git",branch: "main"
                // sh "echo clonning is completed"
                script{
                    clone("https://github.com/rahul6364/notesapp-django.git","main")
                }
            }
        }
        stage ('build'){
            steps{
                // sh "echo this is build step"
                // sh "docker build -t ${IMAGE_NAME}:latest ."
                script{
                    build("notes-app","latest")
                }
            }
        }
        stage ('push to dockerhub'){
            steps{
                // withCredentials([usernamePassword(credentialsId:"dockerhubCred",passwordVariable: "dockerhubPass",usernameVariable:"dockerhubUser")]){
                // sh "echo pushing the images to dockerhub"
                // sh "docker login -u ${env. dockerhubUser} -p ${env.dockerhubPass}"
                // sh "docker image tag notes-app:latest rahul6364/notes-app:latest"
                // sh "docker push ${env. dockerhubUser}/notes-app:latest"
                // }
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
