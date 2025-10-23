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
                    clone("https://github.com/guriwaraich28/django-notes-app.git","b72f8ab")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app","latest","guriwaraich")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","guriwaraich")
                }
            }
        }
        stage("Deploy"){
            steps{
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
