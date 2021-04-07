pipeline {
    agent any
    
    stages{
        stage("CheckOut") {
            steps{
             checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/maan98/sonarrepo.git']]])
            }
        }
         stage('Test') {
            steps {
                sh 'mvn --version'
            }
        }
        stage("SonarQube Analysis") {
            steps {
                sh 'mvn sonar:sonar'
            }
        }
     //    stage('Test sonar code quality') {
        //    steps {
       //        sh 'mvn sonar -f my-app/pom.xml'
     //       }
    //    }
        stage('Deploy') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS' 
              }
            }
            steps {
               echo "successfully depoyed"
            }
        }
    }
}

