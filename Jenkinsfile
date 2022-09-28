node {
    checkout scm
    withEnv(["HOME=${env.WORKSPACE}"]) {
        stage('dependencies') {
            dir('services/ui/angular') {
                docker.image('node:14.16').inside("-e }") {
                    sh 'npm ci --quiet'
                }
            }
        }
        stage('lint') {
            try {
                echo 'linting'
            } catch(Exception e) {
                echo 'Failed linting ' + e.toString()
            }
        }
        stage('build') {
            echo 'Hello World'
        }
    }
}
