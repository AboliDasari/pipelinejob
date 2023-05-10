pipeline{
    agent any
    
    tools {
        maven 'mymaven'
            }
    
    stages{
        
        stage('Git Clone'){
            
            steps{
                git branch: 'main', url: 'https://github.com/AboliDasari/pipelinejob.git'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn install'
            }
        }
        stage('Docker Build'){
            steps{
                sh 'docker build -t abolidasari/myjavaproject10may23 .'
            }
        }
       stage('Docker Push'){
            steps{
                withCredentials([string(credentialsId: 'docker-hub', variable: 'dockerpush')]) {
                sh 'docker login -u abolidasari -p ${dockerpush}'
                }
                 sh 'docker push abolidasari/myjavaproject10may23'
            }
           
        }
        
        
    }
}
