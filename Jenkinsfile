pipeline {
agent any



tools{
maven "DEFAULT"
}



stages {

stage('Hello') {
steps {
echo 'Hello World'
}
}


stage('Build') {
steps {
checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'github credentials', url: 'https://github.com/sreedhar19/javaparser-maven-sample.git']]])
bat 'mvn -B -DskipTests clean package'
}
}
stage('Test') {
steps {

bat 'mvn test -Dmaven.test.failure.ignore=true'
}
}
stage('sonar') {
steps {

bat 'mvn sonar:sonar -Dsonar.login=95ffabcfd0d6ca42dcb392a8b98f3736313dc78d'
}
}
}
}