pipeline {
     agent any
     stages {
        stage("Build") {
            steps {
                sh "npm install"
                sh "npm run build"
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

    }
}