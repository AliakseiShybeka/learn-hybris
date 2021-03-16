def void renameMyFile(pathToSourceFile, newName) {

    if (fileExists(file: pathToSourceFile)) {
        writeFile(file: newName, text: readFile(file: pathToSourceFile))
    }

}




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

                        sh """
                        echo -e 'TEXT = "\n${params.TEXT}'
                        """
                        sh """
                        echo -e '${params.TEXT}' | grep '${params.TEST}'
                       """
                    }
                    else {
                        echo 'oops'
                    }
                }
            }



        }
        stage ('Parallel-demo') {
            steps{
                parallel(
                        a: {
                            writeFile file: 'groovy1.txt', text: 'CHECK = ' + params.CHECK +
                                    '\nTEST = ' + params.TEST +
                                    '\nTEXT = ' + params.TEXT +
                                    '\nCREDS = ' + params.CREDS
                        },
                        b: {
                            git url: 'https://github.com/jfrogdev/project-examples.git'
                        }
                )

            }
        }
        stage ('paralel') {
            parallel {
                stage ('1') {
                    steps {
                        echo '1'
                    }
                }
                stage ('2') {
                    steps {
                        echo '2'
                    }
                }

            }
        }

        stage ('File Rename') {
            steps{
                renameMyFile ('groovy1.txt','newfile.txt')
            }
        }

        stage ('file read') {
            steps {
                echo readFile(file: 'newfile.txt')

            }
        }
        stage('Delete newfile.txt file') {
            steps {
                script {
                    if (fileExists(file: 'newfile.txt')) {
                        echo('yes')
                    } else {
                        echo('newfile.txt file not found')
                    }
                }
            }
        }
    }
}

