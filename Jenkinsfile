import groovy.json.JsonSlurperClassic

def jsonParse(def json) {
    new groovy.json.JsonSlurperClassic().parseText(json)
}
pipeline {
    agent any
    stages {

        stage("paso 1"){
            steps {
                script {
                sh "echo 'Iniciando Proceso'"
                }
            }
        }
        stage("paso 2"){
            steps {
                script {
                sh "echo 'Compilando Código!'"
                sh "./mvnw clean compile -e"
                }
            }
        }
        stage("paso 3"){
            steps {
                script {
                sh "echo 'Testeando Código!'"
                sh "./mvnw clean test -e"
                }
            }
        }
        stage("paso 4"){
            steps {
                script {
                sh "echo 'Empaquetando!'"
                sh "./mvnw clean package -e"
                }
            }
        }
    }
    post {
        always {
            sh "echo 'Fin del proceso'"
        }
        success {
            sh "echo 'Completado Satisfactoriamente'"
        }

        failure {
            sh "echo 'Se Cayó?'"
        }
    }
}