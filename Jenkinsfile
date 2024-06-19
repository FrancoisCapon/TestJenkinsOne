pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }
         stage('Test') {
            steps {
                sh '''
                    # curl --silent https://api.restful-api.dev/objects | grep '{"id":"1","name":"Google Pixel 7 Pro",'
                    curl --silent https://api.restful-api.dev/objects/7 | grep -E '^{"id":"7","name":"Apple MacBook Pro 16","data":{"year":2019,"price":1849.99,"CPU model":"Intel Core i9","Hard disk size":"1 TB"}}$'
                '''
                //script {
                    // assert 10 == 5;
                //}
                 
            }
            
        }
        stage('Test 2') {
            sh 'echo "Not Fail!"; exit 0'
        }
    }
     post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
