pipeline {
  agent { label 'default-jnlp'} 
  stages {
    stage("Import Catalog") {
      steps {
        withCredentials([usernamePassword(credentialsId: 'admin-cli-token', usernameVariable: 'JENKINS_CLI_USR', passwordVariable: 'JENKINS_CLI_PSW')]) {
          sh """
            curl -O http://teams-REPLACE_GITHUB_USERNAME/teams-REPLACE_GITHUB_USERNAME/jnlpJars/jenkins-cli.jar
            alias cli='java -jar jenkins-cli.jar -s http://teams-REPLACE_GITHUB_USERNAME/teams-REPLACE_GITHUB_USERNAME/ -auth $JENKINS_CLI_USR:$JENKINS_CLI_PSW'
            cli pipeline-template-catalogs --put < create-pipeline-template-catalog.json
          """
        }
      }
    }
  }
}