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
                        sh " echo 'TEST = '${params.TEST} "
                        sh " echo 'CHOISE = '${params.CHOISE} "
                        sh " echo 'CREDS = '${params.CREDS} "
                        sh '''
                            echo 'TEXT = '${params.TEXT}
                        '''

                        sh " echo ${params.TEXT} | grep 'line'"
                    }
                    else {
                        echo 'oops'
                    }
                }
            }



        }
    }
}
