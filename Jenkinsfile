pipeline{
    agent{
        label 'hari'
    }
    triggers{
        pollSCM('* * * * *')
    }
    parameters{
        choice(name: 'Branch_Name', choices: ['main', 'fest'], description: 'Selecting branch')
    }
    stages{
        stage('clone'){
            steps{
                git url: 'https://github.com/lahari104/js-e2e-express-server.git',
                    branch: "${params.Branch_Name}"
            }
        }
        stage('build'){
            steps{
                sh """npm install
                      npm run build
                      npm run test
                    """
            }
        }
    }
}