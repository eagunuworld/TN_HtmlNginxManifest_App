node (label: 'TN_HtmlNginx_App'){
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GITHUB') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    //withCredentials([gitUsernamePassword(credentialsId: 'github', gitToolName: 'Default')]) {
   
                    withCredentials([usernamePassword(credentialsId: 'GITHUBID', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email eagunuworld@gmail.com"
                        sh "git config user.name eagunuworld"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+34.174.116.217:8085/repository/primary-argocd.*+34.174.116.217:8085/repository/primary-argocd:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job update manifest: ${env.BUILD_NUMBER}'"
                        sh "git push --force https://$GIT_USERNAME:$GIT_PASSWORD@github.com/$GIT_USERNAME/TN_HtmlNginxManifest_App.git HEAD:walmart-prod"
                        
                        
      }
    }
  }
}
}
