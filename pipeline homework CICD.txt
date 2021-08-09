pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
                git 'https://gist.github.com/b829053c89cfa6686cd4efda68db0aec.git'
            }
        }
        stage('list') {
            steps {
                sh 'ls -lah'
            }
        }
        stage('change ownership') {
            steps {
                sh 'chmod +x mvnInstaller.sh'
            }
        }
        stage('install maven') {
            steps {
                sh 'sudo ./mvnInstaller.sh'
            }
        }
        stage('clone marilena s code') {
            steps {
                git 'https://github.com/MarilenaIstrate/simple-java-maven-app'
            }
        }
        stage('list 2') {
            steps {
                sh 'ls -lah'
            }
        }
        stage('check mvn command') {
            steps {
                sh 'which mvn'
            }
        }
        stage('Build') {
             steps {
                 sh 'mvn -B -DskipTests clean package'
             }
         }
         stage('Test') {
             steps {
                 sh 'mvn test'
             }
             post {
                 always {
                     junit 'target/surefire-reports/*.xml'
                 }
             }
         }
        stage('list final folders') {
            steps {
                sh 'ls -lah ./*'
            }
        }
    }
}