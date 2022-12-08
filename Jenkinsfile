pipeline {
  agent any
  
  
  environment {
    name = 'Lokendra'
  }
  
  
  parameters {
    string(name: 'person', defaultValue: 'Lokendrs Singh', description: 'What should I say?')
    booleanParam(name: 'isMale', defaultValue: 'true', description: "")
    choice(name: 'person', choices: ['Jaipur','Mumbai','Pune'], description: "")
  }
  
  
  stages {
    stage('run a command') {
      steps {
        sh '''
        ls
        date
        pwd
        cal 2022
        '''
      }
    }
    stage('Environment Variable') {
      environment {
        username = 'myusername'
      }
      steps {
        sh 'echo "${BUILD_ID}"'
        sh 'echo "$(name)"'
        sh 'echo "$(username)"'
      }
    }
    stage('Parameters') {
      steps {
        echo 'deploy on test'
        sh 'echo "${name}"'
        sh 'echo "${person}"'
      }
    }
    stage('Continue ?') {
      steps {
        Input (message: 'Should we continue')
        ok 'yes we Should'
        echo 'deploy on prod'
      }
    }
    stage('deploy on prod') {
      steps {
        echo 'deploy on prod'
      }
    }
  }
  
  
  post {
    always {
        echo ' I will always say hello again '
    }
    failure {
        echo ' failure '
    }
    success {
        echo ' success '
    }
  }
}
