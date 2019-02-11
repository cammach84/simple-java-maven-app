pipeline {
    //agent {
    //    docker { image 'node:7-alpine' }
    //}

    agent any

    parameters {
        string(name: 'myname', defaultValue: 'Tony', description: 'How should I greet the world?')
    }

    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'sqlite'
    }

    stages {
        stage('Cam Mach - First Stage - Build') {
            steps {
                retry(3) {
                    sh 'echo "########### Execute Retry #########"'
                    sh './sayhello.sh'
                }

                timeout(time: 5, unit: 'SECONDS') {
                    sh 'echo "########## Reach Timeout step#############"'
                }

		        sh 'echo "Hello world from My Jenkins file! OK! OK! OK!#########"'
                sh 'mvn -B -DskipTests clean package'
            }
        }

        stage ('Cam Mach - Second Stage - Test') {
            steps {
                sh 'mvn test'
            }

            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }

        stage('Parameters Example') {
            steps {
                sh 'echo "Hello, ${myname}!"'
            }
        }

        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }

        stage('Sanity check') {
            steps {
                input "Does the staging environment look OK?"
            }
        }


        stage('Cam Mach - Final Stage') {
           steps {
                sh 'echo "########### END OF SIMPLE PIPELINE ##############"'
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
