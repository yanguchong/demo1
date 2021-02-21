pipeline {
     agent any
     stages {
        stage("Build") {
            steps {
                sh "sudo npm install"
                sh "sudo npm run build"
            }
        }
        stage("Deploy") {
            steps {
                withAWS(region: 'us-west-2', credentials: 'creds_for_aws'){
                    s3Upload(bucket:'yangs-website-demo', 
                        path: 'demo1/',
                        workingDir:'build', 
                        includePathPattern:'**/*')
                }
            }
        }
        // stage("Deploy") {
        //     steps {
        //         sh "sudo rm -rf /var/www/jenkins-react-app"
        //         sh "sudo cp -r ${WORKSPACE}/build/ /var/www/jenkins-react-app/"
        //     }
        // }
    }
}