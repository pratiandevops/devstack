pipeline {
    agent {label 'Ubuntu'}
    parameters {
            booleanParam(name: 'Rebuild_LMSImage', defaultValue: false, description: 'Will Rebuild LMS Image')
            booleanParam(name: 'Rebuild_CMSImage', defaultValue: false, description: 'Will Rebuild CMS Image')
    }

    stages {
        stage ('Rebuild LMSImage') {
                      when {
                             expression { params.Rebuild_LMSImage == true }
                      }
                      steps {
                              sh 'make lms-static'
                      }
        }
        stage ('Rebuild CMSImage') {
                      when {
                             expression { params.Rebuild_CMSImage == true }
                      }
                      steps {
                              sh 'make studio-static'
                      }
        }

        stage ('Deployment Conatiner') {
            steps {
                    sh 'make down'
                    sh 'make dev.up'
            }
        }
    }
}
