node {
  checkout scm
  stage('Build') {
    echo 'Hello World'
  }
  stage('Lint') {
    try {
      echo 'linting'
    } catch(Exception e) {
      echo 'Failed linting ' + e.toString()
    }
  }
}
