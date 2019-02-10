pipeline {
    agent any
    stages {
        stage('#######Cam Mach - First Stage#############') { 
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
	stage('#######Cam Mach - Second Stage#############') {
	   steps {
		sh 'echo "########### END OF Stage 2 ##############"'
	   }
	}
    }
}
