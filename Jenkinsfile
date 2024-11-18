pipeline{
    agent any

    environment{
        NODE_VERSIONS = '18.x'
    }
    tools{
        nodejs "${NODE_VERSIONS}"
    }

    stage{
        ('Checkout'){
            steps{
                git branch: 'main', url:'https://github.com/KatyaPenkova/StudentRegistryAppDemo'
            }
        }

        stage("Install dependeies"){
            steps{
                script{
                        bat 'npm install'
                    }
                }   
            }
        }

        stage("Start application and run tests")
        {
            steps{
                script{
                    bat 'npm start &'
                    bat 'wait-on http://localhost:8090'
                    bat 'npm test'
                }
            }
        }
    }

    post {
        always{
            echo "CI pipepline completed"
        }
    }
}
