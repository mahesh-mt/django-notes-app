@Library("Shared") _
pipeline{
    agent {label "slave"}
    stages{
        stage("code"){
            steps{
                script{
                    clone("https://github.com/mahesh-mt/django-notes-app.git","main")
                }
                echo "code clonning successful"
            }
        }
        stage("build"){
            steps{
                script{
                    docker_build("note-app","latest","maheshtathod")
                }
                echo "code Build successful"
            } 
        }
        
        stage("Push to docker hub"){
            steps{
                script{
                    docker_push("note-app","latest","maheshtathod")
                }
                echo "Image Push successfully"
            }
            
        }
        
        stage("Deploy"){
            steps{
                echo 'This is deploying the code'
                sh "docker compose down && docker-compose up -d"
            }
        }
    }
    
} 
