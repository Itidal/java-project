properties([pipelineTriggers([githubPush()])])

node('linux') { 
    stage('Unit Tests') {
        git 'https://github.com/Itidal/java-project.git'
        sh 'ant -f test.xml -v' 
    }
    stage('Build') { 
        sh 'ant -f build.xml -v'
    }
    
stage('Results') {
    junit 'reports/*.xml' }
}
