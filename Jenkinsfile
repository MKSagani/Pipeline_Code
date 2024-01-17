pipeline {
    agent any
     tools {
        maven 'Maven3' 
        }
    stages {
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
                
                
            }
            
        }
        stage("Build"){
            steps{
                sh "mvn package"
                
            }
            
        }
        stage("Deploy on Test"){
           steps {
           deploy adapters: [tomcat9(credentialsId: 'tomcat9details', path: '', url: 'http://51.21.130.163:8080/')], contextPath: '/app', war: '**/*.war'
        }
            
        }
        stage("Deploy on Prod"){
             input {
                message "Should we continue?"
                ok "Yes we Should"
            }
            
                // deploy on container -> plugin
               steps {
             deploy adapters: [tomcat9(credentialsId: 'tomcat9details', path: '', url: 'http://13.51.69.21:8080/')], contextPath: '/app', war: '**/*.war'

        }

        }
    }
    
}
