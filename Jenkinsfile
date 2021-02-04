pipeline {
  agent any
  stages {
   
    stage('Build') {
      steps { 
        sh 'cd ~/workspace/graf/ && terraform apply -auto-approve && sleep 1m' 
      }
    }
    
    stage('Provision') {
      steps { 
        sh 'cd /etc/ansible && ansible graf -m shell -a "docker pull grafana/grafana" -i vultr.yml && ansible graf -m shell -a "docker run -d --name=grafana -p 3000:3000 grafana/grafana" -i vultr.yml'
      }
    }
    
  }
}
