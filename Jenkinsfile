node {
    docker.image('node:16-buster-slim').inside('-p 3000:3000') {
        stage('Build') {
            sh 'npm install'
        }
        stage('Test') {
            sh './jenkins/scripts/test.sh'
        }
        stage('ManualApproval') {
            input message: 'Lanjutkan ke Tahap Deploy?'
        }
        stage('Deploy') {
            sh './jenkins/scripts/deliver.sh'
            sleep(time:60,unit:"SECONDS")
            sh './jenkins/scripts/kill.sh'
        }
    }
}
