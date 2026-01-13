pipeline {
   agent none

   environment {
    AUTHOR = "ANDI NAILAH MASHFUFAH SULFA"
    EMAIL = "105841116623@student.unismuh.ac.id"
    WEB = "https://www.unismuh.ac.id"
   }
   
   opsions {
    disableConcureentBuilds()
    timeout(time: 10, unit: 'MINUTES')
   }

    stages {
        
        stage("Prepare") {
             environment{
                APP = credentials("nayol_park")
             }
             agent {
        node {
            label "Linux && java17"
        }
    }
            steps {
                echo("AUTHOR ${AUTHOR}")
                echo("EMAIL ${EMAIL}")
                echo("WEB ${WEB}")
                echo("Start Job : ${env.JOB_NAME}")
                echo("Start Build : ${env.BUILD_NUMBER}")
                echo("Start Name : ${env.BRANCH_NAME}")
                echo("App User : ${APP_USR}")
            }
        }

        stage("Build") {
             agent {
        node {
            label "Linux && java17"
        }
    }
            steps {

                script{
                    for (int i = 0; i < 10; i++) {
                        echo("Script ${i}")
                    }
                }
                echo ('Start Build')
                sh("./mvnw clean compile test-compile")
                echo ('Finish Build')
            }
        }

        stage('Test') {
             agent {
        node {
            label "Linux && java17"
        }
    }
            steps {

                script {
                    def data = [
                        "firstName" : "Park",
                        "lastName" : "Nayol"
                    ]
                    writeJSON(file: "data.json", json: data)
                }
                echo ('Start test')
                sh("./mvnw test")
                echo ('Finish test')
            }
        }

        stage('Deploy') {
             agent {
        node {
            label "Linux && java17"
        }
    }
            steps {
                echo ('Hello Deploy 1')
                sleep(5)
                echo ('Hello Deploy 2')
                echo ('Hello Deploy 3')
            }
        }
    }

    post{
        always {
            echo "I will always say Hello again!"
        }
        success {
            echo "Yay, success"
        }
        failure {
            echo "Oh no, failure"
        }
        cleanup {
            echo "Don't care success or error"
        }
    }
}