
// checking docker image name
if (env.BRANCH_NAME == 'master') {
  image = "1.0.${BUILD_NUMBER}"
} else if (env.BRANCH_NAME == 'dev') {
  impact = "GIT_COMMIT"
} else if (env.BRANCH_NAME == 'staging') {
  impact = "medium"
} else {
  impact = "unknown"
}



pipeline {

    agent any


    stages { 
        stage('build') {
            when {
                expression { BRANCH_NAME =~ /^(master$)/}
            }
            steps{
                script{
                    echo "${impact}"
                    //sh "docker build -t 1.0.${BUILD_NUMBER} ."
                }
            }
        }
    }

}
