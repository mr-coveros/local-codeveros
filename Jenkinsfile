node {
    stage('cleanup') {
        cleanWs()
    }
    checkout scm
    dir('services/ui/angular') {
        stage('dependencies') {
            docker.image('node:14.16').inside() {
                sh 'npm ci --quiet --cache="./npm"'
            }
        }
#        stage('lint') {
#            docker.image('node:14.16').inside() {
#                try {
#                    sh 'npm run checkstyle --cache="./npm"'
#                } catch(Exception e) {
#                    echo 'Failed linting ' + e.toString()
#                }
#            }
#        }
#        stage('test') {
#            docker.image('buildkite/puppeteer:8.0.0').inside() {
#                sh 'npm run test --cache="./npm"'
#            }
#        }
        stage('build') {
            docker.image('node:14.16').inside() {
                sh 'npm run build.production --cache="./npm"'
            }
        }
        stage('deliver') {
            if("${env.BRANCH}" == 'master') {
                docker.withRegistry(credentialsId: 'dockerhub') {
                    def myImage = docker.build("mrcoveros/codeveros-ui:${env.BUILD_ID}")
                    myImage.push()
                    myImage.push(latest)
                }
            }
        }
    }
}
