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
                sh "echo gradle"
                /*sh "chmod +x gradlew"*/
                /*sh "../IonicApp/android/gradlew clean"  
                sh "../IonicApp/android/gradlew assembleDebug"*/
            }
        }
      }
   }
