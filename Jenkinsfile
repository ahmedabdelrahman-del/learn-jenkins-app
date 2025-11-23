pipeline {
    agent any
    stages {
        stage('Build'){
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps{
                sh'''
                ls -la
                node --version
                npm --version
                npm ci
                npm run build
                ls -la
                '''
            }
        }
        stage('Test'){

            steps{
                script{
                    def exist = fileExists('build/index.html')
                    if (exist){
                        echo "file is fine"

                    }else{
                        echo "file is failed"
                        
                    }
  
                }
            }
        }

    }
}
