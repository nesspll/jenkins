pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello World"'
                 sh '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
             }
         }
         stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e *.html'
              }
         }
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-west-2',credentials:'87a95d19-bfa8-4420-aadf-c16ca1e3a8bd') {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(file:'index.html', bucket:'static-jenkins-pipeline2')
                  }
              }
         }
     }
}
