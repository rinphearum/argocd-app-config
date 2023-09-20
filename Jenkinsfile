pipeline {
  agent any
  stages {
    stage('Update dockerfile') {
      steps {
      script {
        catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github-cred', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')])  {
                        
                        sh "git config user.email phearumrin34@gmail.com"
                        sh "git config user.name rinphearum"
                        sh "sed -i \"s+phearum/react-jenkin.*+phearum/react-jenkin:${BUILDTAG}+g\" dev/myapp-deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/argocd-app-config.git HEAD:main"
          
        }
      }
      }
  }
}
}
}