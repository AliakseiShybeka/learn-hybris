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
        stage ('File Rename') {
            steps{
                renameMyFile ("groovy1.txt")
            }
        }
    }
}

def void renameMyFile(pathToSourceFile) {

    if (fileExists(file: pathToSourceFile)) {
        def newFile = "newfile.txt"

        writeFile(file: newFile, encoding: "UTF-8", text: readFile(file: pathToSourceFile, encoding: "UTF-8"))
    }

}