pipeline {
    agent any
    stages {
        stage('#######Cam Mach - ccBuild#############') { 
            steps {
		sh 'echo "Hello world from My Jenkins file! OK! OK! OK!#########"'
                sh 'mvn -B -DskipTests clean package' 
            }
        }
    }
}
