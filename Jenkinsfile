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
                        echo '========================'
                        echo '=   check is enabled   ='
                        echo '========================'
                        echo ${params.TEST}
//                        echo 'CHOOSE = '${params.}
                    }
                    else {
                        echo 'fuck'
                    }
                }
            }



        }
    }
}
