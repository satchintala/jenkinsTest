pipeline {
    agent any

    stages {
        stage('Install') {
            steps {
                echo 'Install Dependencies'
                script{
                    if (isUnix()){
                        sh 'npm install'
                    }else{
                        bat 'npm install'
                    }
                }               
            }
        }
        stage('Execute') {
            steps {
                echo 'Execute Tests'
                script{
                    if (isUnix()){
                        sh 'npm test'
                    }else{
                        bat 'npm test'
                    }
                }  
            }
        }
        stage('Report') {
            steps {
                echo 'Run Report'
                script{
                    if (isUnix()){
                        sh 'npm run report'
                    }else{
                        bat 'npm run report'
                    }
                }  
            
            }
        }
        stage('Publish Report') {
            steps {
                echo 'Publish Report'
                publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'report', reportFiles: 'cucumber_report.html', reportName: 'Cucumber HTML Report', reportTitles: '', useWrapperFileDirectly: true])
            }
        }
    }
}
