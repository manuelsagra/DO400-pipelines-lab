pipeline {
    agent any

    parameters {
        booleanParam (name: "RUN_INTEGRATION_TESTS", defaultValue: true)
    }

    stages {
        stage('Test') {
            paralell {
                stage('Unit Tests') {
                    steps {
                        sh './mvnw test -D testGroups=unit'
                    }
                }

                stage('Integration tests') {
                    when  {
                        expression { return params.RUN_INTEGRATION_TESTS }
                    }
                    
                    steps {
                        sh './mvnw test -D testGroups=integration'
                    }
                }
            }
        }
    }
}