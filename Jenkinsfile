pipeline {
    agent any

    stages {
        steps {
                withSonarQubeEnv('SonarQubePruebas'){
                    // If you are using Windows then you should use "bat" step
                    // Since unit testing is out of the scope we skip them
                    sh "mvn -B clean deploy sonar:sonar"
                }
            }
        stage("Quality Gate"){
            steps{
                timeout(time: 2, unit: 'MINUTES'){
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}
