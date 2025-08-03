pipeline {
  agent any

//   tools {
//     maven 'maven-3.8.7'   // Set this to whatever Maven version is configured in Jenkins (or remove if using system Maven)
//   }

  stages {
    stage('Clone') {
      steps {
        git url: 'https://github.com/Naman2608/task-manager.git', branch: 'master'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }

    stage('Deploy') {
      steps {
        sh 'ansible-playbook -i ansible/inventory.ini ansible/deploy.yml'
      }
    }
  }

  post {
    success {
      echo '✅ Build and Deployment successful!'
    }
    failure {
      echo '❌ Build or Deployment failed!'
    }
  }
}

