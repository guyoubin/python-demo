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
            sh 'cd /root/Jenkins/workspace/python_pipeline && coverage run *.py && coverage xml && pylint --rcfile="pylint.conf" *.py > report.txt'
            sh 'sonar-scanner -Dsonar.host.url=http://192.168.195.138:9000 -Dsonar.projectKey=python-demo -Dsonar.projectName=python-demo -Dsonar.sources=. -Dsonar.sourceEncoding=UTF-8 -Dsonar.language=py -Dsonar.python.coverage.reportPath=*coverage*.xml -Dsonar.python.pylint=pylint -Dsonar.python.pylint_config=pylint.conf -Dsonar.python.pylint.reportPath=report.txt'
         }
      }
   }
}
