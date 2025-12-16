pipeline {
    agent any

    stages {

        stage('Stage-2-Test-Artifact-No-ComponentId') {
            steps {
                script {
                    echo "Testing artifact without componentId in <ENV>"

                    registerBuildArtifactMetadata(
                        name: "test-service-${env.BUILD_NUMBER}-test-2",
                        version: "1.0.${env.BUILD_NUMBER}",
                        type: 'docker',
                        url: "https://registry.example.com.in-2/test-service:1.0.${env.BUILD_NUMBER}",
                        digest: "sha256:${UUID.randomUUID().toString().replace('-','')}",
                        label: 'test1'
                    )
                }
            }
        }

        stage('Stage-3-Test-Artifact-With-ComponentId') {
            steps {
                script {
                    echo "Testing artifact with componentId in <ENV>"

                    registerBuildArtifactMetadata(
                        name: "test-service-${env.BUILD_NUMBER}-test",
                        version: "1.0.${env.BUILD_NUMBER}",
                        type: 'docker',
                        url: "https://registry.example.com.in/test-service:1.0.${env.BUILD_NUMBER}",
                        digest: "sha256:${UUID.randomUUID().toString().replace('-','')}",
                        label: 'test1-with-comp',
                        componentId: '196effd4-cb50-459d-b46d-290b723064e5'
                    )
                }
            }
        }
    }
}
