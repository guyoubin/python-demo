pipeline {
   agent any
   stages {
      stage('Poll SCM') {
         steps {
            git url: 'https://github.com/guyoubin/python-demo.git'
         }
      }
      stage('Static Code Analysis') {
         steps {
            sh 'cd python-demo && coverage run *.py && coverage xml'
            sh 'sonar-scanner -Dsonar.host.url=http://192.168.195.138:9000'
         }
      }
   }
}
