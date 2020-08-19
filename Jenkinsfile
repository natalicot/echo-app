
pipeline {

    agent any


    stages { 
        stage('build') {
            if (env.BRANCH_NAME == 'master'){
                docker build -t 1.0.${BUILD_NUMBER} .
            } else {
                docker build -t dev-${GIT_COMMIT_HASH} .
            }



            // when {
            //     expression { BRANCH_NAME =~ /^(master$)/}
            // }
            // steps{
            //     script{
            //         sh "docker build -t 1.0.${BUILD_NUMBER} ."
            //     }
            // }
            // when {
            //     expression { BRANCH_NAME =~ /^(dev$)/}
            // }
            // steps{
            //     script{
            //         sh "docker build -t dev-${GIT_COMMIT_HASH} ."
            //     }
            // }
            // when {
            //     expression { BRANCH_NAME =~ /^(staging$)/}
            // }
            // steps{
            //     script{
            //         sh "docker build -t staging-${GIT_COMMIT_HASH} ."
            //     }
            // }
        }

        
        // stage('E2E_test'){
        //     when {
        //         expression { BRANCH_NAME =~ /^(master$|feature\/*)/}
        //     }
        //     agent {
        //         docker {
        //             image 'python:2.7'
        //             args'--network toxictypo_default'
        //         }
        //     }   
        //     steps{
        //         script{
        //             withEnv(["HOME=${env.WORKSPACE}"]) {
        //                 sh 'pip install -r src/test/requirments.txt'
        //                 sh "python src/test/e2e_test.py runtest:8080 src/test/sanity"
        //             }
        //         }
                
        //     }
            
        // }
        // stage('publish') {
        //     when {
        //         expression { BRANCH_NAME =~ /^(master$)/}
        //     }
        //     steps {
        //         script{
        //             sh 'docker tag test:latest 614864356236.dkr.ecr.us-east-2.amazonaws.com/toxictypoapp:latest'
        //             docker.withRegistry('https://614864356236.dkr.ecr.us-east-2.amazonaws.com', 'ecr:us-east-2:toxictypoapp') {
        //                 sh "docker push 614864356236.dkr.ecr.us-east-2.amazonaws.com/toxictypoapp:latest"
        //             }
        //         }
        //     }
        // }
        // stage('deploy') {
        //     when {
        //         expression { BRANCH_NAME =~ /^(master$)/}
        //     }
        //     steps {
        //         script {
        //             sshagent(['ec2']){
        //                 sh "ssh -o StrictHostKeyChecking=no -l ec2-user ec2-3-20-236-91.us-east-2.compute.amazonaws.com 'docker pull 614864356236.dkr.ecr.us-east-2.amazonaws.com/toxictypoapp:latest && docker rm -f toxictypoapp || true && docker run --name toxictypoapp -d -p 8080:8080 614864356236.dkr.ecr.us-east-2.amazonaws.com/toxictypoapp:latest'"
        //             }
        //         }
        //     }
        // }
    }
    // post { 
    //     // always { 
    //     //     sh 'docker rm -f runtest || true'
    //     // }
    //     failure {
    //         updateGitlabCommitStatus state: 'failed'
    //     }
    //     success {
    //         updateGitlabCommitStatus state: 'success'
    //     }
    // }
    
}
