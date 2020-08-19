
// checking docker image name

if (env.BRANCH_NAME == 'master') {
  image = "1.0.${BUILD_NUMBER}"
} else if (env.BRANCH_NAME == 'dev') {
  image = "GIT_COMMIT"
} else if (env.BRANCH_NAME == 'staging') {
  image = "GIT_COMMIT"
} else {
  image = "unknown"
}

// pipline:

pipeline {

    agent any


    stages { 
        stage('build') {
            steps{
                script{
                    sh "docker build -t ${image} ."
                }
            }
        }
    }

}
