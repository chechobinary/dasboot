
node {

    try {
        notify('Started')
        stage('Checkout') {
            checkout scm
        }

        stage('build') {
            def mvn_version = 'M3'
            withEnv(["PATH+MAVEN=${tool mvn_version}/bin"]) {
                sh 'mvn clean install'
            }
        }

        notify('Success')

    } catch (err) {
        notify("Error: ${err}")
        currentBuild.result = 'FAILURE'

    }
}

def notify(status){
    emailext (
            to: "you@gmail.com",
            subject: "${status}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
            body: """<p>${status}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
        <p>Check console output at <a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a></p>""",
    )
}