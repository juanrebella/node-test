pipeline {
    agent any
    
    environment{
        
        DOCKERHUB_CREDENTIALS=credentials('dockerhub')
    }
    
                stages{
                    
                        stage ('Build Docker Image') {
                            
                                    steps{
                                        sh "docker build -t nacho/nodetest:$BUILD_NUMBER ."
                                    }
                        }
                        
                        stage ('Docker Hub Login') {
                                    
                                    steps{
                                        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                                    }
                        }
                        
                        stage('Docker push Image'){
                            
                                    steps{
                                        sh 'docker push nacho/nodetest:$BUILD_NUMBER'
                                    }
                        }
                }
}
