pipeline {
    agent any

//    environment {
//        CHECK = 'true'
//        TEST = ''
//    }

    stages {
        stage('Build') {
            steps {
                script {
                    if (params.CHECK) {
                        echo 'hello'
                    }
                    else {
                        echo 'fuck'
                    }
                }
            }



        }
    }
}
