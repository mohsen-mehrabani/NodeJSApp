pipeline {
        agent {
            dockerfile {
                filename 'Dockerfile.dev'
                dir 'client'
                args {
                    '-v /app/node_modules'
                    '-v ./client:/app'
                }
            }
            dockerfile {
                filename 'Dockerfile.dev'
                dir 'nginx'
            }
            dockerfile {
                filename 'Dockerfile.dev'
                dir 'server'
                args {
                    '-v /app/node_modules'
                    '-v ./server:/app'
                }
            }
            dockerfile {
                filename 'Dockerfile.dev'
                dir 'worker'
                args {
                     '-v REDIS_HOST=redis'
                     '-v REDIS_PORT=6379'
                }
            }
            docker {
                image 'redis'
            }
            docker {
            image 'postgres'
            args  '-v POSTGRES_PASSWORD=postgres_passwordp'
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