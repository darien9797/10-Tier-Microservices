pipeline {
    agent any

    stages {
        stage('Git') {
            steps {
                git branch: 'main', url: 'https://github.com/darien9797/10-Tier-Microservices.git'
            }
        }
        
        
        stage('adservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier-Microservices/src/adservice/') {
                                 sh "docker build -t darien97/adservice:latest ."
                                 sh "docker push darien97/adservice:latest"
                        }
                    }
                }
            }
        }
		
		stage('cartservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier-Microservices/src/cartservice/src/') {
                                 sh "docker build -t darien97/cartservice:latest ."
                                 sh "docker push darien97/cartservice:latest"
                        }
                    }
                }
            }
        }
		
		stage('checkoutservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier-Microservices/src/checkoutservice/') {
                                 sh "docker build -t darien97/checkoutservice:latest ."
                                 sh "docker push darien97/checkoutservice:latest"
                        }
                    }
                }
            }
        }
		
		stage('currencyservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier-Microservices/src/currencyservice/') {
                                 sh "docker build -t darien97/currencyservice:latest ."
                                 sh "docker push darien97/currencyservice:latest"
                        }
                    }
                }
            }
        }
        
		stage('emailservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier-Microservices/src/emailservice/') {
                                 sh "docker build -t darien97/emailservice:latest ."
                                 sh "docker push darien97/emailservice:latest"
                        }
                    }
                }
            }
        }
		
		stage('frontend') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier-Microservices/src/frontend/') {
                                 sh "docker build -t darien97/frontend:latest ."
                                 sh "docker push darien97/frontend:latest"
                        }
                    }
                }
            }
        }
		
		stage('loadgenerator') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier-Microservices/src/loadgenerator/') {
                                 sh "docker build -t darien97/loadgenerator:latest ."
                                 sh "docker push darien97/loadgenerator:latest"
                        }
                    }
                }
            }
        }
		
		stage('paymentservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier-Microservices/src/paymentservice/') {
                                 sh "docker build -t darien97/paymentservice:latest ."
                                 sh "docker push darien97/paymentservice:latest"
                        }
                    }
                }
            }
        }
        
		stage('productcatalogservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier-Microservices/src/productcatalogservice/') {
                                 sh "docker build -t darien97/productcatalogservice:latest ."
                                 sh "docker push darien97/productcatalogservice:latest"
                        }
                    }
                }
            }
        }
		
		stage('recommendationservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier-Microservices/src/recommendationservice/') {
                                 sh "docker build -t darien97/recommendationservice:latest ."
                                 sh "docker push darien97/recommendationservice:latest"
                        }
                    }
                }
            }
        }
		
		stage('shippingservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                          dir('/var/lib/jenkins/workspace/10-Tier-Microservices/src/shippingservice/') {
                                 sh "docker build -t darien97/shippingservice:latest ."
                                 sh "docker push darien97/shippingservice:latest"
                        }
                    }
                }
            }
        }
        
        stage('K8') {
            steps {
               withKubeConfig(caCertificate: '', clusterName: '', contextName: '', credentialsId: 'k8-secret-eks', namespace: 'devops', restrictKubeConfigAccess: false, serverUrl: 'https://3F82B1EA239BEA2B37CC8262E86B654A.gr7.ap-southeast-1.eks.amazonaws.com') {
                       sh "kubectl apply -f deployment-service.yml"
					   sh "kubectl get pods -n devops"
					   sh "kubectl get svc -n devops"
               }
            }
        }


    }
}
