pipeline{
    agent any
    tools{
        maven "Maven-3.9.8"
        jdk 'Java-17'
    }

    environment{
        BUILD_FILE = 'Appserverfile'
        ROLE = "Developer"
        NAME = "Jayant"
    }
    stages{
        stage('Clean and Build the code'){
            steps{
                sh '''
                mvn --version
                mvn build package
                mvn compile
                '''
            }
        }
        stage('Building the docker Image and Run Container'){
            steps{
                sh '''
                docker build -t jayant700/maven-docker-app02 .
                docker conatiner run --name project03 -it jayant700/maven-docker-app02
                '''
            }

        }
         stage("Pushing the job in Dockerhub"){
            steps{
                sh '''
                docker login -u jayant700 -p Jayant@123
                docker push jayant700/maven-docker-app02:latest
                '''
            }

        }
         stage("Testing the Job"){
            steps{
                echo "Testing"
            }

        }



    }


}
