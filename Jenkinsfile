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
                        sh """
                        echo '========================'
                        echo '=   check is enabled   ='
                        echo '========================'
                        echo 'CHOOSE = '${params.TEST}
                    """


//
                    }
                    else {
                        echo 'fuck'
                    }
                }
            }



        }
    }
}
