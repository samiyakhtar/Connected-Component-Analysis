pipeline {
    agent { docker { image 'shahatuh/dp2306' } }

    environment {
        PATH = "env/bin/:$PATH"
    }
    stages {
        stage('build') {
            steps {
                sh 'python ca-02.py -i Images/hubble.ppm -t 128 -d 0'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'output/**/*.* ', onlyIfSuccessful: true
        }
    }
}
