@Library("Shared") _
pipeline{
    agent { label "agent-1"}
    stages{
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                clone("https://github.com/arkapratimsarkar/django-notes-app.git","main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                docker_build("notes-app","latest","arkapratim")
                }
            }
        }
        stage("Test"){
            steps{
                echo "This is testing the code"
            }
        }
        stage("Push to Docker Hub"){
            steps{
                script{
                    docker_push("notes-app","latest","arkapratim")
                }
            }
        }
        stage("Deploy"){
            steps{
                script{
                    docker_compose()
                }
            }
        }
    }
}
