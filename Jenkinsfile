pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    triggers {
        githubPush()
    }

    stages {

        stage('Clean Target Folder') {
            steps {
                sh '''
                mkdir -p /home/jenkins/deploy
                rm -rf /home/jenkins/deploy/*
                '''
            }
        }

        stage('Checkout') {
            steps {
                git branch: 'develop',
                    url: 'https://github.com/SupradeepanK/addressbook.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Copy Files') {
            steps {
                sh '''
                cp -r * /home/jenkins/deploy/
                '''
            }
        }

        stage('Verify') {
            steps {
                sh 'ls -l /home/jenkins/deploy/'
            }
        }
    }
}
