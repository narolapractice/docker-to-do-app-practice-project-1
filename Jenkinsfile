@Library("Shared") _
pipeline {
    agent { label "worker1" }
    
    stages {
        stage("Greet"){
            steps{
                script{
                  hello()   
                }
            }
        }
        stage("Clone"){
            steps{
                script{
                 clone("https://github.com/narolapractice/docker-to-do-app-practice-project-1.git", "master")   
                }
            }
        }
        stage("Push Image to DockerHub"){
            steps{
                script{
                    push_to_dockerhub("djangocicd-django","latest","ads754792")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
