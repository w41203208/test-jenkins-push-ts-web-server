pipeline {
  agent { node { label "Main" } }
  environment { 
    BRANCH_TYPE = 'test'
  }
  stages {
    stage('Check') {
      when {
        branch 'test-*'
      }
      steps {
        script {
          BRANCH_TYPE='test'
        //   sh '''
        //     env.BRANCH_TYPE=test
        //   '''
        }
        // echo TEST=${TEST}
        // echo BUILD_ID=${env.BUILD_ID}
        // echo BUILD_NUMBER=${env.BUILD_NUMBER}
        // echo BUILD_TAG=${env.BUILD_TAG}
        // echo BUILD_URL=${env.BUILD_URL}
        // echo EXECUTOR_NUMBER=${env.EXECUTOR_NUMBER}
        // echo JAVA_HOME=${env.JAVA_HOME}
        // echo JENKINS_URL=${env.JENKINS_URL}
        // echo JOB_NAME=${env.JOB_NAME}
        // echo NODE_NAME=${env.NODE_NAME}
        // echo WORKSPACE=${env.WORKSPACE}
      }
    }
    stage('Fix-Feature') {
      when {
        branch 'fix-*'
      }
      steps {
        script {
          BRANCH_TYPE='fix'
        //   sh '''
        //     env.BRANCH_TYPE=fix
        //   '''
        }
      }
    }
    stage('Dev') {
      when {
        branch 'dev-*'
      }
      steps {
        BRANCH_TYPE=dev
        sh "printenv"
        // script {
        //   env.BRANCH_TYPE = 'dev'
        // }
      }
    }
    // stage('Checkout') {
    //   steps {
    //     git branch: 'dev', url: 'https://github.com/w41203208/test-build-server.git'
    //   }
    // }
    stage('Build') {
      steps {
        echo "----------- Build ${env.BRANCH_TYPE} -----------"
        echo "Hello, ${env.BRANCH_TYPE}"
      }
    }
    stage('Deploy') {
      when {
        branch 'main'
      }
      steps {
        script {
          sh '''
            BRANCH_TYPE='main'
          '''
        }
      }
    }
  }
}