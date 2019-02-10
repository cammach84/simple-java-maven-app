pipeline {
    agent {
        docker { image 'node:7-alpine' }
    }
    stages {
        stage('am Mach - First Stage') {
            steps {
                retry(3) {
                    sh 'echo "########### Execute Retry #########"'
                    sh './sayhello.sh'
                }

                timeout(time: 5, unit: 'SECONDS') {
                    sh 'echo "########## Reach Timeout step#############"'
                }

		        sh 'echo "Hello world from My Jenkins file! OK! OK! OK!#########"'
                //sh 'mvn -B -DskipTests clean package'
            }
        }

        stage('Cam Mach - Second STage') {
            steps {
                sh 'echo "Fail!"; exit 1'
            }
        }

        stage('Cam Mach - Third Stage') {
            steps {
                sh 'node --version'
            }
        }

        stage('Cam Mach - Final Stage') {
           steps {
                sh 'echo "########### END OF Stage 2 ##############"'
           }
        }
    }

    post {
        always {
            echo 'This will always run'
        }

        success {
            echo 'This will run on Success'
        }

        failure {
            echo 'This will run on Failure'
        }

        unstable {
            echo 'This will run only if the run was marked as unstable'
        }

        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
