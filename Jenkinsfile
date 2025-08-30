// #!groovy
// pipeline {
//   agent none
//   stages {
//     stage('Maven Install') {
//       agent {
//         docker {
//           image 'maven:3.5.0'
//         }
//       }
//       steps {
//         sh 'mvn clean install'
//       }
//     }
//     stage('Docker Build') {
//       agent any
//       steps {
//         sh 'docker build -t grupo01/spring-petclinic:latest .'
        
//       }
//     }
//   }
// }

#!groovy
pipeline {
  agent none
  stages {
    stage('Maven Install') {
      agent {
        docker {
          image 'maven:3.5.0'
        }
      }
      steps {
        sh 'mvn clean install'
      }
    }
    stage('Docker Build') {
      agent {
        docker {
          image 'docker:latest'  // Usa una imagen con Docker CLI
          args '-v /var/run/docker.sock:/var/run/docker.sock'  // Monta el socket
        }
      }
      steps {
        sh 'docker build -t grupo01/spring-petclinic:latest .'
      }
    }
  }
}