pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                    parallel(
                        a: {
                            echo "This is branch a"
                        },
                        b: {
                            echo "This is branch b"
                        })
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}

