pipeline{
        agent any
        stages{
            stage('Install '){
                steps{
                    sh "rm -rf https://gitlab.com/wacdevops/chaperootodo_client.git"
                    sh "git clone https://gitlab.com/wacdevops/chaperootodo_client.git
                  ~"
                    
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
                    sh "sudo docker-compose pull && sudo -E DB_PASSWORD=password123 docker-compose up -d"
                }
            }
        }
}
