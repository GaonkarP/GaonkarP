pipeline {
    agent any

    stages {
        stage('Build') {
            steps {script{
                echo 'Building..'
                echo 'test'
                dir("build"){deleteDir()}
                dir("build"){
                    echo "build directory created"
                }
                cmd = "pyinstaller ${env.WORKSPACE}/day_detail.py"
                sh label: 'Build', returnStatus: true, script: cmd

            }}
        }
        stage('Test') {
            steps {script{
                echo 'Testing..'
                if(isUnix()){
                    echo 'Unix Agent..'
                    sh label: 'Build', returnStatus: true, script: 'python day_detail.py'
                }else{
                    bat label: 'Build', returnStatus: true, script: 'python day_detail.py'
                }
            }}
        }
        stage('Run') {
            steps {
                echo 'Running in test directory....'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
