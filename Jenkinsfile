pipeline {
    agent any
    options {
        buildDiscarder logRotator(daysToKeepStr: '5', numToKeepStr: '10')
    }
    stages {
        stage('npm install') { 
            steps {

                sh "npm install"
            }
        }
        stage('android') {
            steps {
                sh "rm -rf android"
                sh "npx cap add android"
            }
        }
       stage('build') {
            steps {

                sh "npm run build"
            }
        }
      
       stage('sync') {
            steps {

                sh "npx cap sync"
            }
        }
       stage('gradle') {
            steps {
                sh "../Demo/android/gradlew clean"  
                sh "../Demo/android/gradlew assembleDebug"
            }
        }
      }
   }
