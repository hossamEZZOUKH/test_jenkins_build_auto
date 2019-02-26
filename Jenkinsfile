#!/usr/bin/en groovy
node { 
      def mvnHome 
      stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      //git 'https://hosssamezzoukh@bitbucket.org/hosssamezzoukh/jenkins_test.git'
      // Get the Maven tool. ** NOTE: This 'M3' Maven tool must be configured ** in the global configuration.
      mvnHome = tool 'MAVEN3' 
     echo 'fin du stage preparation'
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) { 
      sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package" 
      echo 'le maven build Unix '
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Results') { 
      junit '**/target/surefire-reports/TEST-*.xml' 
      echo 'test unitaire ' 
      archive 'target/*.jar' 
      
   }
}
