pipeline {
    agent {
        node {
            label 'AGENT-1'  
        }
    }
    
     environment { 
        GREETING = 'Hello Jenkins'
    }

    options {
        ansiColor('xterm')
        // timeout(time: 1, unit: 'HOURS')
        // disableConcurrentBuilds()
    }
        parameters {
        string(name: 'version', defaultValue: '1.0.0', description: 'Who should I say hello to?')
        string(name: 'environment', defaultValue: '', description: 'Who should I say hello to?')
       
    }
    stages {
        stage('print version') {
            steps {
                echo "${params.version}"
                echo "${params.environment}"
            
        }
        }
        stage('check params'){
            steps{
                sh """
                    echo "Hello ${params.PERSON}"

                    echo "Biography: ${params.BIOGRAPHY}"

                    echo "Toggle: ${params.TOGGLE}"

                    echo "Choice: ${params.CHOICE}"

                    echo "Password: ${params.PASSWORD}"
                """
            }
        }
    }
    // post build
    post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()
        }
        failure { 
            echo 'this runs when pipeline is failed, used generally to send some alerts'
        }
        success{
            echo 'I will say Hello when pipeline is success'
        }
    }
}
}