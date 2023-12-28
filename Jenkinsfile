pipeline {
    agent any

    environment {
        PATH = "$PATH:/usr/local/bin"
    }

    stages {
        stage('Checkout') {
            steps {
                // Krok: Pobierz kod źródłowy z repozytorium
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Krok: Utwórz wirtualne środowisko i zainstaluj zależności
                sh 'python3 -m venv venv'
                sh 'source venv/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                // Krok: Uruchom testy jednostkowe
                sh 'source venv/bin/activate && python -m unittest discover'
            }
        }

        stage('Deploy') {
            steps {
                // Tutaj można dodać kroki związane z wdrażaniem aplikacji
                // na środowisko produkcyjne, jeśli to ma sens dla projektu.
            }
        }
    }

    post {
        always {
            // Krok: Zawsze dezaktywuj wirtualne środowisko po ukończeniu
            sh 'deactivate || true'
        }
    }
}