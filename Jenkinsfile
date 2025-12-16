pipeline {
    agent any

    stages {
        stage('Stage-3-Test-Artifact-ComponentId') {
            steps {
                script {
                    echo "Testing componentId parameter in <ENV>"

                    registerBuildArtifactMetadata(
                        name: "test-service-${env.BUILD_NUMBER}",
                        version: "1.0.${env.BUILD_NUMBER}",
                        type: 'docker',
                        url: "https://registry.example.com/test-service:1.0.${env.BUILD_NUMBER}",
                        digest: "sha256:${UUID.randomUUID().toString().replace('-','')}",
                        label: 'test',
                        componentId: '196effd4-cb50-459d-b46d-290b723064e5'
                    )
                }
            }
        }
    }
}
