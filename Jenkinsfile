pipeline {
    agent { label 'maven' }
    stages {
        stage('GIT') {
            steps {
                echo 'Getting Project from Git'
                git branch: 'main', credentialsId: 'acces_git', url: 'https://github.com/salmakhiari/devops.git'
            }
        }

        stage('Login dockerhub') {
            steps {
                sh 'sudo chmod 777 /var/run/docker.sock'
                sh 'docker login -u salamlam -p dckr_pat_BY7jONdJoD1O0a1i1xsA5N9UTS0'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
     //    stage('JUNIT') {
        //    steps {
         //   sh 'mvn clean test -Dtest=com.esprit.examen.services.FournisseurServiceImplTest -Dmaven.test.failure.ignore=true'
         //   }
       // }

//  stage('MOCKITO') {
//   steps {
//  sh 'mvn clean test -Dtest=com.esprit.examen.services.FournisseurServiceImplMock'
//   }
//   }*/
/*
         stage('Jacoco') {
            steps {
                sh 'mvn clean jacoco:prepare-agent package'
            }
        }*/

       // stage('SonarQube') {
       //     steps {
       //         sh "mvn sonar:sonar -Dsonar.login=squ_6d91055b96eb44c55e1646262f6fa8707a5690c8 -DskipTests"
         //   }
        //}

       // stage('Nexus') {
         //   steps {
          //      sh "mvn deploy -DskipTests"
           // }
       // }
       // */

        stage('Build image') {
            steps {
                sh 'docker build -t tpexam .'
            }
        }

        stage('docker compose') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
/*    post {
            success {
                 mail to: "chedli.elloumi@esprit.tn",
                 subject: "success",
                 body: "success on job ${env.JOB_NAME}, Build Number: ${env.BUILD_NUMBER}, Build URL: ${env.BUILD_URL}"
            }
    failure {
                mail to: "chedli.elloumi@esprit.tn",
                 subject: "Failure",
                 body: "Failure on job ${env.JOB_NAME}, Build Number: ${env.BUILD_NUMBER}, Build URL: ${env.BUILD_URL} "
    }
    }*/
}
