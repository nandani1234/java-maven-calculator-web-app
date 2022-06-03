node {
   docker.image('maven:3.8.5-openjdk-8').inside('-v /root/.m2:/root/.m2') {
      stage('Checkout Code') {
         git 'https://github.com/nandani1234/java-maven-calculator-web-app.git'
      }
      stage('JUnit Test') {
         sh "mvn clean test"
      }
      stage('Integration Test') {
         sh "mvn integration-test"
      }
      /*
         stage('Performance Test') {
            sh "mvn cargo:start verify cargo:stop"
         }
      */
      stage('Performance Test') {
         sh "mvn verify"
      }
      stage('Deploy') {
         timeout(time: 10, unit: 'MINUTES') {
            input message: 'Deploy this web app to production ?'
         }
         echo 'Deploy...'
      }
   }
}