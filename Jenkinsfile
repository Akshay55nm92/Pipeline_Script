pipeline {
    agent any
    stages {
        stage('Git-Checkout') {
            steps {
                echo "Checking out from Git Repository Groovy Script";
                git 'https://github.com/Akshay55nm92/Pipeline_Script.git'
            }
        }
        stage('Compile') {
            steps {
                echo "Compiled Successfully!! Groovy Script";
                sh './Build.sh'
            }
        }

        stage('JUnit') {
            steps {
                echo "JUnit passed Successfully Groovy Script";
                sh label: '', script: './Unit.sh'
            }
        }

        stage('Quality-Gate') {
            steps {
                echo "SonarQube Quality-Gate passed Successfully Groovy Script";
                sh label: '', script: './Quality.sh'
            }
        }

        stage('Deploy') {
            steps {
                echo "Pass Groovy Script";
                sh label: '', script: './Deploy.sh'
            }
        }
    }

    post { 
        always {
            echo "This will always run"
        }
        success {
            echo "This will run only if successful"
        }
        failure {
            echo "This will run only if failed"
        }
        unstable {
            echo "This will run only if the run was marked as unstable"
        }
        changed {
            echo "This will run only if the the state of the pipeline has changed"
            echo "Example, If the pipeline was previously failing but is now Successful"
        }
    }
}
