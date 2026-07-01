@Library('my-gradle-library') _

pipeline {
    agent any
    tools {
        jdk 'jdk17'
    }
    stages {
        stage('Compile & Build') {
            steps {
                gradleBuild()
            }
        }
        
        // Di sinilah optimasi paralel terjadi
        stage('Parallel Tests & Analysis') {
            parallel {
                stage('Unit Testing') {
                    steps {
                        gradleTest()
                    }
                }
                stage('Static Code Analysis') {
                    steps {
                        // Contoh jika menggunakan Checkstyle / SonarQube / PMD
                        echo "Menjalankan analisis kualitas kode..."
                        // sh './gradlew checkstyleMain'
                        sh 'sleep 10'
                    }
                }
            }
        }
    }
}