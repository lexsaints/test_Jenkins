pipeline {
    
     agent{
        label "192.168.154.145"
    }

    stages {
        stage('pull code1') {
            steps {
                echo "======================="
                echo 'pull code'
                echo "${env.JOB_BASE_NAME}"
                echo "${env.JOB_NAME}"
                echo "${env.BUILD_DISPLAY_NAME}"
                echo "${env.BRANCH_NAME}"
                echo "${env.NODE_NAME}"
                echo "================="
                sh 'echo $PATH'
                sh 'java -version'
                sh 'whoami & pwd'
            }
		}
        stage('pull code') {
            steps {
                echo 'pull code'
				checkout([$class: 'GitSCM', branches: [[name: '*/${branch}']], extensions: [], userRemoteConfigs: [[credentialsId: '2e1475f9-0089-4875-aecf-993219c3311d', url: 'https://github.com/lexsaints/mvnwebapp.git']]])     
            }
        }
        stage('build') {
            steps {
                echo 'mvn build'
                sh 'echo $PATH'
                sh 'whoami'
                sh 'pwd'
                sh 'mvn clean package'
            }
        }
        stage('deploy') {
            steps {
                echo 'deploy'

                // sh 'cp /var/lib/jenkins/workspace/p1/target/mvnwebapp.war /var/www/webapps/'
            }    
        }
        stage('publish') {
            steps {
                echo 'publish'
                deploy adapters: [tomcat8(credentialsId: 'b9d03141-db2c-4d0e-9698-e662ea912354', path: '', url: 'http://192.168.154.133:8088')], contextPath: null, war: 'target/*.war'            }    
        }
    }
    post{
        always{
            echo '112121212'
        }
    }
}
