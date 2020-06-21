pipeline {
  agent none
  stages {
    stage('Build & Compile') {
      agent any
      steps {
        git 'https://github.com/Bomidi/time-tracker.git'
      }
    }

    stage('Test') {
      agent any
      steps {
        echo 'testing...'
      }
    }

    stage('Approval') {
      steps {
        script {
          def deploymentDelay = input id: 'Deploy', message: 'Deploy to production?', submitter: 'rkivisto,admin', parameters: [choice(choices: ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11', '12', '13', '14', '15', '16', '17', '18', '19', '20', '21', '22', '23', '24'], description: 'Hours to delay deployment?', name: 'deploymentDelay')]
          sleep time: deploymentDelay.toInteger(), unit: 'HOURS'
        }

      }
    }

    stage('Deploy') {
      agent any
      steps {
        lock(resource: 'deployApplication') {
          echo 'Deploying...'
        }

      }
    }

  }
}