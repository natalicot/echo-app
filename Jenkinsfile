
// checking docker image name



// pipline:

pipeline {

    agent any
    
    stages { 
      stage('build') {
        if (env.BRANCH_NAME == 'master') {
          image = "1.0.${BUILD_NUMBER}"
        } else if (env.BRANCH_NAME == 'dev') {
          image = "dev-$GIT_COMMIT"
        } else if (env.BRANCH_NAME == 'staging') {
          image = "staging-$GIT_COMMIT"
        } else {
          image = "unknown"
        }
        steps{
          script{
            sh "docker build -t natalicot/echo-app:${image} ."
          }
        }
      }
      stage('deploy') {
        steps{
          script{
            withCredentials([[$class: 'UsernamePasswordMultiBinding',credentialsId: 'docker_hub',usernameVariable: 'USER',passwordVariable: 'PASSWORD']]){
              sh "docker login -u $USER -p $PASSWORD"
              sh "docker push natalicot/echo-app:${image}"
            }
          }
        }
      }
    }

}
