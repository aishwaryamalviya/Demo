pipeline {
    agent any
    options {
        buildDiscarder logRotator(daysToKeepStr: '5', numToKeepStr: '10')
    }
    stages {
        stage('npm install') { 
            steps {

                cmd "npm install"
            }
        }
        stage('android setup') {
            steps {
                cmd "rm -rf android"
                cmd "npx cap add android"
            }
        }
       stage('build app') {
            steps {

                cmd "npm run build"
            }
        }
      
       stage('sync with android') {
            steps {

                cmd "npx cap sync"
            }
        }
       /*stage('build android') {
            steps {
                sh "export ANDROID_HOME=/var/lib/jenkins/android-sdk"
                sh "export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64"
                cmd "cd /var/lib/jenkins/workspace/Demo/android && ./gradlew clean"  
                cmd "cd /var/lib/jenkins/workspace/Demo/android && ./gradlew assembleDebug"
            }
        }*/
      }
   }
