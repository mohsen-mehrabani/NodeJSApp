pipeline {
    agents{
        agent {
            dockerfile {
                filename 'Dockerfile.dev'
                dir 'client'
                args {
                    '-v - /app/node_modules'
                    '-v - ./client:/app'
                }
            }
        }
        agent {
            dockerfile {
                filename 'Dockerfile.dev'
                dir 'nginx'
            }
        }            
        agent {
            dockerfile {
                filename 'Dockerfile.dev'
                dir 'server'
                args {
                    '-v - /app/node_modules'
                    '-v - ./server:/app'
                }
            }
        }    
        agent {
            dockerfile {
                filename 'Dockerfile.dev'
                dir 'worker'
                args {
                     '-v - REDIS_HOST=redis'
                     '-v - REDIS_PORT=6379'
                }
            }
        }    
        agent {
            docker {
                image 'redis'
            }
        }            
        agent {
            docker {
            image 'postgres'
            args  '-v - POSTGRES_PASSWORD=postgres_passwordp'
            }
        }
    
    }
    stages {
        stage('Back-end') {
            agent {
                docker { image 'maven:3-alpine' }
            }
            steps {
                sh 'mvn --version'
            }
        }
        stage('Front-end') {
            agent {
                docker { image 'node:14-alpine' }
            }
            steps {
                sh 'node --version'
            }
        }
    }
    }
}