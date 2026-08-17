pipeline {
    agent any
 
    stages {
        stage('SCM Checkout') {
            steps {
                echo 'Git Clone'
                git branch: 'main', 
                credentialsId: 'Github-ID', 
                url: 'https://github.com/deepankiaqin-alt/sonarqube.git'
            }
        }
        stage('Code Coverage') {
            steps {
                sh 'echo "This is sonarqube task perfect"'
            }
        }
        stage('Sonarqube Analysis') {
            steps {
                script {
                    def scannerhome = tool name: 'sonar-scanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
                    
                withCredentials([string(credentialsId: 'sonar-token', variable: 'SONAR_TOKEN')]) {
                    sh """
                            ${scannerhome}/bin/sonar-scanner \
                            -Dsonar.projectKey=deepan0808 \
                            -Dsonar.sources=app.js \
                            -Dsonar.host.url=http://172.31.14.116:9000 \
                            -Dsonar.login=$SONAR-TOKEN
                       """
                    }
                
                } 
            }
        }
          
    }
}
