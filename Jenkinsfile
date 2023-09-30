node {
    // Menggunakan Docker Agent
    docker.image('node:16-buster-slim').withRun("-p 3000:3000") {
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
