pipeline {
    agent any

    stages {
        stage('Git') {
            steps {
                git branch: 'main', url: 'https://github.com/ons26/devops'
            }
        }
         stage('Build') {
            echo '→ Étape de build'
            // 👉 adapte selon ton projet
            if (fileExists('pom.xml')) {
                echo 'Projet Maven détecté'
                sh 'mvn -B -DskipTests clean package'
                archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            } else if (fileExists('package.json')) {
                echo 'Projet Node.js détecté'
                sh 'npm ci'
                sh 'npm run build --if-present'
                archiveArtifacts artifacts: 'dist/**', allowEmptyArchive: true
            } else {
                error "Aucun outil de build détecté (ni pom.xml ni package.json)"
            }
        }

    }
     
}
