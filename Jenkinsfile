pipeline{
        agent any
        stages{
            stage('Clone Repo'){
                steps{
                    sh "rm -rf https://gitlab.com/qacdevops/chaperootodo_client.git"
                    sh "git clone https://gitlab.com/qacdevops/chaperootodo_client.git"
                  
                    
                }
            }    
            stage('Install Docker'){
                steps{
                    sh "whoami"
                    sh "sudo usermod -aG sudo jenkins"
                    sh "chmod +x docker-install.sh && chmod +x docker-compose.sh"
                    sh "./docker-install.sh"
                    sh "sudo usermod -aG docker jenkins"
                    sh "./docker-compose.sh"
                    
                }
            }
            stage('Run App'){
                steps{
                    sh "export DB_PASSWORD=password123"
                    sh "sudo docker-compose -f chaperootodo_client/docker-compose.yaml pull && sudo -E DB_PASSWORD=password123 docker-compose -f chaperootodo_client/docker-compose.yaml up -d"
                }
            }
        }
}
