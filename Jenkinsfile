node {
    stage('cleanup') {
        cleanWs()
    }
    checkout scm
    stage('dependencies') {
        dir('services/ui/angular') {
            docker.image('node:14.16').inside('-u root') {
                try {
                    sh 'npm ci --quiet'
                } catch(Exception e) {
                    echo 'Failed installing dependencies ' + e.toString()
                    sh 'cat /root/.npm/_logs/*.log'
                }
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
