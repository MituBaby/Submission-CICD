node {
    def customImage = 'node:16-buster-slim'
    def customArgs = '-p 3000:3000'

    // Menggunakan Docker Agent
    docker.image(customImage).withRun("-p 3000:3000") {
        // Stage Build
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }

        // Stage Test
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
    }
}
