pipeline{
        agent any
        stages{
            stage('Build'){
                steps{
                    sh '''
                    docker build -t mnduoflask:latest .
                    '''
                }
            }
            stage('Push'){
                steps{
                    sh '''
                    docker tag mnduoflask gcr.io/lbg-python-cohort-8/mnduoflask:latest
                    docker push gcr.io/lbg-python-cohort-8/mnduoflask:latest
                    '''
                }
            }
            stage('Deploy'){
                steps{
                    sh '''
                    kubectl apply -f . # instead of period can have a line for kubectl apply -f [each yaml file]
                    '''
                }
            }
            stage('Cleanup'){
                steps{
                    sh '''
                    docker system prune -a --force
                    '''
                }
            }
        }
}