pipeline {
    agent any
     tools{
        maven '3.9.0'
     }
    stages {
          stage('Build Maven'){

            steps{
            checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Abuzar-Mehdi/devops-automation']])
            bat 'mvn clean install'
            }

          }

    stage('Build docker image'){
            steps{
                script{
                    bat 'docker build -t abuzar14/devops-integration .'
                }
            }
        }

     stage('Push image to Hub'){
            steps{
                script{

                    bat 'docker login -u abuzar14 -p Ubl@906234/?'

                   bat 'docker push abuzar14/devops-integration'
                }
            }
        }

    }

}
