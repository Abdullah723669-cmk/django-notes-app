@Library("Shared") _
pipeline {
    agent { label "mamun" }

    stages {
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code") {
            steps {
                script{
                    clone('https://github.com/Abdullah723669-cmk/django-notes-app.git','main')
                }
            }
        }

        stage("Build") {
            steps {
                script{
                    docker_build("notes-app","latest","mamun723")
                }
            }
        }

        stage("Push") {
            steps {
                script{
                    docker_push("notes-app","latest","mamun723")   
                }
            }
        }

        stage("Deploy") {
            steps {
                echo "MY Django App is deploying now ... ..."
                // Use docker-compose (depends on installation)
                sh 'dokcer compose down && docker compose up -d'
                echo "My Django Notes-App is deployed successfully !!"
            }
        }

    
    }
}
