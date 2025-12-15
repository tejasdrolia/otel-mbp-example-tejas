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
                        componentId: 'REPLACE_WITH_COMPONENT_ID_FROM_CBP'
                    )
                }
            }
        }
    }
}
