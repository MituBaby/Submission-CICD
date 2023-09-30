node {
    // Menggunakan Docker Agent
    def customImage = 'node:16-buster-slim'
    def customArgs = '-p 3000:3000'

    checkout scm

    try {
        // Stage Build
        stage('Build') {
            steps {
                script {
                    docker.image(customImage).withRun(customArgs) {
                        sh 'npm install'
                    }
                }
            }
        }

        // Stage Test
        stage('Test') {
            steps {
                script {
                    docker.image(customImage).inside(customArgs) {
                        sh './jenkins/scripts/test.sh'
                    }
                }
            }
        }
    } finally {
        // Clean up Docker container (optional)
        script {
            docker.image(customImage).stop()
            docker.image(customImage).remove()
        }
    }
}
