pipeline {
    agent any

    stages {
        stage('Stage 0') {
            steps {
                echo 'Done with stage 0'
            }
        }
        stage('Stage 1') {
            steps {
                echo 'Waiting a bit'
                sh "sleep 10"
                echo 'Done with stage 1'
            }
        }
        stage('Stage 2') {
            steps {
                echo 'Waiting a bit'
                sh "sleep 5"
                echo 'Done with stage 2'
            }
        }
    }
}
