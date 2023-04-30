node (label: 'TN_HtmlNginx_App'){
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GITHUB') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    //withCredentials([gitUsernamePassword(credentialsId: 'github', gitToolName: 'Default')]) {
   
                    withCredentials([string(credentialsId: 'argocd-token-connection', variable: 'fixed')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email eagunuworld@gmail.com"
                        sh "git config user.name eagunuworld"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+eagunuworld/primary-argocd.*+eagunuworld/primary-argocd:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job update manifest: ${env.BUILD_NUMBER}'"
                        sh "git push --force https://$fixed@github.com/eagunuworld/TN_HtmlNginxManifest_App HEAD:walmart-prod"
                        
                        
      }
    }
  }
}
}
