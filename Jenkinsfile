node('maven'){
    def mvnhome = tool name: 'maven360', type: 'maven'
    stage('first stage checkout'){
        git credentialsId: 'gitToken', url: 'https://github.com/deepaklama0815/Khatra_Jenkins.git'
        echo "first staggggge1"
    }
    stage('maven build'){
        sh "$mvnhome/bin/mvn clean test surefire-report:report-only"
    }
   
    stage('running junit for test report'){
        junit : 'target/surefire-reports/*.xml'
        publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '/home/ec2-user/jenkins_workspace/ex1/workspace/new_Project/target/surefire-reports', reportFiles: 'index.html', reportName: 'HTMLReport', reportTitles: ''])
    }
     stage('packaging software'){
        sh "$mvnhome/bin/mvn clean package"
    }
    
    stage('Archiving the completed jar file'){
        archiveArtifacts '**/target/*.jar'
    }
}
