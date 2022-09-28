node {
    checkout scm
    docker.image('nodejs:14.16').pull
    docker.image('nodejs:14.16').inside {
        stage('dependencies') {
            dir('services/ui') {
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
