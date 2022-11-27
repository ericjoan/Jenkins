pipeline {
    agent any

    stages {
        stage("Quality Gate"){
            steps{
                timeout(time: 2, unit: 'MINUTES'){
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}
