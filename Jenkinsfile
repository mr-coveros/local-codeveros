node {
    checkout scm
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
