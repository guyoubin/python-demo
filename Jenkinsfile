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
            sh 'cd /root/Jenkins/workspace/python_pipeline && coverage run *.py && coverage xml'
            sh 'sonar-scanner -Dsonar.host.url=http://192.168.195.138:9000'
         }
      }
   }
}
