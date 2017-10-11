
node {
    stage('Checkout') {
        checkout scm
    }

    stage('build') {
        sh 'mvn clean build'
    }
}