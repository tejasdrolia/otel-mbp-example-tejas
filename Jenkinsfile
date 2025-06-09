pipeline {
    agent any
    stages {
        stage('Stage-0') {
            steps {
                withMockLoad(averageDuration: 3, testFailureIgnore: false) {
                    sh MOCK_LOAD_COMMAND
                }
            }
        }
        stage('1') {
            parallel {
                stage('Stage-1.1') {
                    steps {
                        sh "echo 'first step'"
                        withMockLoad(averageDuration: 3, testFailureIgnore: false) {
                            sh MOCK_LOAD_COMMAND
                        }
                        sh "echo 'Execution completed'"
                    }
                }
                stage('Stage-1.2') {
                    stages {
                        stage('1.2.1') {
                            steps {
                                withMockLoad(averageDuration: 9, testFailureIgnore: false) {
                                    sh MOCK_LOAD_COMMAND
                                }
                            }
                        }
                        stage('1.2.2') {
                            steps {
                                withMockLoad(averageDuration: 9, testFailureIgnore: false) {
                                    sh MOCK_LOAD_COMMAND
                                }
                            }
                        }   
                    }
                }
            }
        }
        stage('Stage-3') {
            steps {
                withMockLoad(averageDuration: 5, testFailureIgnore: false) {
                    sh MOCK_LOAD_COMMAND
                }
            }
        }
    }
}
