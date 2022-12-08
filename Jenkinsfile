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
                    
                    sh "sudo -s apt-get update && sudo apt install curl -y"
                    sh "curl https://get.docker.com | sudo bash"
                    sh 'sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose'
                    sh "sudo chmod +x /usr/local/bin/docker-compose"
                    sh "jenkins ALL= NOPASSWD: ALL"
                    
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
