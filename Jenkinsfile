node {
   
   stage('Code Checkout') { // for display purposes
      // Get some code from a GitHub repository
git credentialsId: '9c5600a6-c0d3-4e81-a2b3-cca6d7257abb', url: 'https://github.com/pavants52/java-app.git'
   }
   stage('Build') {
     withMaven(jdk: 'java-1.8.0-openjdk-amd64 ', maven: 'apache-maven-3.5.2') {
       sh 'mvn clean compile'
     }
   }
   stage('Unit Test') {
     withMaven(jdk: 'java-1.8.0-openjdk-amd64 ', maven: 'apache-maven-3.5.2') {
       sh 'mvn test'
     }
   }
   stage('SonarQube Analysis') {
      //def job = build job: 'SonarJob'
      //withSonarQubeEnv("SonarQube") {
     withMaven(jdk: 'java-1.8.0-openjdk-amd64 ', maven: 'apache-maven-3.5.2') {
        sh 'mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent package sonar:sonar ' +
          ' -Dsonar.host.url=https://sonarcloud.io '+
          ' -Dsonar.organization=pavants52 ' +
         ' -Dsonar.login=14c72f2b1ec1fe86f3de48d9e2e7fe8ee3ebe804 ' 
        }
      //}
     }
    stage('Archival') {
     withMaven(jdk: 'java-1.8.0-openjdk-amd64 ', maven: 'apache-maven-3.5.2') {
       sh 'mvn package'
     }
   }
     stage('Deploy to Artifactory Repo') {
     withMaven(jdk: 'java-1.8.0-openjdk-amd64 ', maven: 'apache-maven-3.5.2') {
     }
     }
   
    stage('Deploy to Dev') {
     withMaven(jdk: 'java-1.8.0-openjdk-amd64 ', maven: 'apache-maven-3.5.2') {
      //junit '**/target/surefire-reports/TEST-*.xml'
      //archive 'target/*.jar'
   }
    }
   stage('Smoke Test Execution') {
     withMaven(jdk: 'java-1.8.0-openjdk-amd64 ', maven: 'apache-maven-3.5.2') {
      //junit '**/target/surefire-reports/TEST-*.xml'
      //archive 'target/*.jar'
   }
   }
    
   stage('Smoke Test Execution') {
     withMaven(jdk: 'java-1.8.0-openjdk-amd64 ', maven: 'apache-maven-3.5.2') {
      //junit '**/target/surefire-reports/TEST-*.xml'
      //archive 'target/*.jar'
    }
   }
}
