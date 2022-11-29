pipeline {
    agent any
    stages {
        
        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('SonarQubePruebas') {
                    bat "mvn clean verify sonar:sonar"
                }
            }
        }
        stage("Quality gate") {
            steps {
                timeout(time: 2, unit: 'MINUTES'){
                    waitForQualityGate abortPipeline: true
                }
            }
        }
        post{
            sucess{
                bat "chrome /incognito http://localhost:8080/job/Tareas%203%20de%20diciembre/job/DesplegarProduccion/build?token=963852"
                bat "echo Tarea Iniciada correctamente"
            }
            failure{
                bat "chrome /incognito http://localhost:8080/job/Tareas%203%20de%20diciembre/job/Notificar/build?token=789456"
                timeout(time: 5, unit: 'SECONDS'){
                    bat "taskkill /F /IM Chrome.exe"
                }
            }
        }
    }
}
