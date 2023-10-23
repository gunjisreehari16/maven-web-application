pipeline {
    agent any 
    stages {
        stage ("git clone"){
            steps {
                script {
                    git url: 'https://github.com/gunjisreehari16/maven-web-application.git', branch:'master'
                    
                }
            }
        }
        stage("mvn"){
            steps {
                script {
                    sh "mvn clean package"
                }
            }
        }
        stage("docker build "){
            steps {
                script {
                    sh "docker build -t gsreehari/mavenapp:6 ."
                }
            }
        }
    
    stage ("docker login"){
        steps {
            script {
                sh " docker login -u gsreehari -p camp@1122"
            }
        }
    }
    stage("docker push"){
        steps {
            script {
                sh "docker push gsreehari/mavenapp:1"
            }
        }
    }
    }
}
