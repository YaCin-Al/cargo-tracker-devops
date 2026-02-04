pipeline {
    agent any

    triggers {
        githubPush()   
    }

    stages {

        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/YaCin-Al/cargo-tracker-devops.git'
            }
        }

        stage('Build & Test with Coverage') {
            steps {
                withmaven(maven: 'Maven 3.8.4') {
                    bat 'mvn clean verify'
                }
            }
        }

        
    }
//
    post {
        success {
            echo 'Build et analyse terminés avec succès !'
        }
        failure {
            echo 'Échec du build ou des tests.'
        }
    }
}
