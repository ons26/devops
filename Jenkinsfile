pipeline {
    agent any

    stages {
        stage('Git') {
            steps {
                git branch: 'main', url: 'https://github.com/ons26/devops'
            }
        }
         stage('Build') {
               steps {
          build 'ons Arctic 10 pip'
               }

    }
     
}
}
