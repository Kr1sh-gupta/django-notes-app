@Library("Shared") _
pipeline{
    agent {label "agent-rookie"}
    
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
                    
                clone("https://github.com/Kr1sh-gupta/django-notes-app.git" ,"main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                docker_build("notes-app","latest","kr1sh")   
                }
            }
        }
        stage("Test"){
            steps{
                echo "This testing the code"
            }
        }
        stage("Pushing to DockerHub"){
            steps{
               script{
                   docker_push("notes-app","latest","kr1sh")
               }
            }
        }
        stage("Deploy"){
            steps{
                 echo "This deploying the code"
                //  sh "docker run -d -p 8000:8000 notes-app:latest"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
