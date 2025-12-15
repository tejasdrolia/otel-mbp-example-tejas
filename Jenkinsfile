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
        stage('Test Artifact with ComponentId') {
              steps {
                  script {
                      echo "Testing componentId parameter in <ENV>"

                      // Test 1: WITH componentId
                      registerBuildArtifactMetadata(
                          name: "test-service-${env.BUILD_NUMBER}",
                          version: "1.0.${env.BUILD_NUMBER}",
                          type: 'docker',
                          url: "https://registry.example.com/test-service:1.0.${env.BUILD_NUMBER}",
                          digest: "sha256:${UUID.randomUUID().toString().replace('-','')}",
                          label: 'test',
                          componentId: 'REPLACE_WITH_COMPONENT_ID_FROM_CBP'  // ← IMPORTANT!
                      )
                      echo "✓ Artifact registered with componentId"

                      // Test 2: WITHOUT componentId (default behavior)
                      registerBuildArtifactMetadata(
                          name: "default-service-${env.BUILD_NUMBER}",
                          version: "2.0.${env.BUILD_NUMBER}",
                          type: 'maven'
                      )
                      echo "✓ Artifact registered with default component"
                  }
              }
          }        
    }
}
