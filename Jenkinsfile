CODE_CHANGES = getGitChanges()
pipeline {
    agent any
    parameters {
         string(name: 'VERSION', defaultValue: '', description: 'Version to deploy on project')
         choice(name: 'VERSION', choices: ['1.1.0','1.2.0','1.3.0']
         booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    environment {
          NEW_VERSION = '1.3.0'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                ECHO "building version ${NEW_VERSION}"
            }
        }
        stage('Test') {
            when {
                expression {
                     BRANCH_NAME == 'main' && CODE_CHANGES == true
            }
    
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            when {
                expression {
                     params.executeTests
                }
            }
            steps {
                echo 'Deploying....'
            }
        }
    }
    post {
        always {
            echo 'Completed'
        }
        failure {
             echo 'Failed'
        }
        success {
             echo 'Successful'
        }
     }
}
