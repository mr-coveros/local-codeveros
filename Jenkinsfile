node {
    stage('cleanup') {
        cleanWs()
    }
    checkout scm
    stage('dependencies') {
        dir('services/ui/angular') {
            docker.image('node:14.16').inside('-u root') {
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
