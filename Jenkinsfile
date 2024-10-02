pipeline {
    agent any

    environment {
        // Définit la variable d'environnement pour Maven
        MAVEN_HOME = '/usr/share/maven'
        JAVA_HOME = '/usr/lib/jvm/java-17-openjdk-17.0.12.0.7-2.el9.x86_64/bin/java'
        PATH = "${MAVEN_HOME}/bin:${JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                // Vérifie le code depuis le dépôt (Git par exemple)
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Commande pour nettoyer et compiler le projet Maven
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                // Commande pour exécuter les tests Maven
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                // Commande pour packager l'application (générer le .jar ou .war)
                sh 'mvn package'
            }
        }

        stage('Archive Artifacts') {
            steps {
                // Archive le fichier .jar ou .war généré
                archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            }
        }

        stage('Deploy') {
            steps {
                // Exemple étape de déploiement (à adapter selon ton environnement)
                // sh 'mvn deploy'
                echo 'Déploiement...'
            }
        }
    }

    post {
        success {
            // Notification ou action en cas de succès du pipeline
            echo 'Build réussi !'
        }

        failure {
            // Notification ou action en cas d'échec
            echo 'Le build a échoué.'
        }
    }
}
