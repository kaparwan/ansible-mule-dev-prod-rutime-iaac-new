/* groovylint-disable CompileStatic, DuplicateStringLiteral, SpaceAfterMethodCallName, SpaceInsideParentheses */
pipeline {
  agent any

      environment {
        USER_CREDENTIALS = credentials('anypoint-login-credentials')
        ANYPOINT_USERNAME = "${env.USER_CREDENTIALS_USR}"
        ANYPOINT_PASSWORD = "${env.USER_CREDENTIALS_PSW}"
      }


    stages {
        stage('Env Variables') {
      steps {
        echo "The build number is ${env.BUILD_NUMBER}"
        echo "You can also use \${BUILD_NUMBER} -> ${BUILD_NUMBER}"
        sh 'echo "I can access $BUILD_NUMBER in shell command as well."'
      }
        }

    stage('provision runtime dev and prod' ) {
      steps {
        sh 'export PATH="$PATH:/usr/local/bin";export $ANYPOINT_USERNAME; export $ANYPOINT_PASSWORD'
        sh 'cd ./deploy; ./run.sh'
      }
    }

    }
}
