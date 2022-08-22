pipeline {
    agent any

    triggers{
            pollSCM '* * * * *'
    }
    stages {
        stage('initws') {
            steps {
                //clean workspace before init
                echo "cleanws"
                cleanWs()
            }
        }
        
        stage('getinit') {
            steps {
                //get init
                echo "gitinit"
                git branch: 'main', url: 'https://github.com/Elad0109/simple-webapp-nodejs-.git'
            }
        }  

        stage('build') {
            steps {
                echo 'build'
                nodejs('nodejs 18.7') {
                   // run build
                   sh 'npm install'
                }
            }
        }
        
        stage ('test') {
            steps {
                echo 'test'
                nodejs('nodejs 18.7') {
                    ///run build
                    sh 'npm run test'
                }
            }
        }
    }
}
