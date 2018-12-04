properties([pipelineTriggers([githubPush()])])

node('linux') { 
    stage('Unit Tests') {
        git 'https://github.com/Itidal/java-project.git'
        sh 'echo Build URL is $BUILD_URL, Build Number: $BUILD_NUMBER'
        sh 'ant -f test.xml -v' 
    }
    stage('Build') { 
        sh 'ant -f build.xml -v'
    }
    stage('Deploy') {
        sh 'aws s3 cp dist/rectangle-${BUILD_NUMBER}.jar s3://itidal-assignment-10/' 
    }
}
