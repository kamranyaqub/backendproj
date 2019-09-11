pipeline {
agent any
environment {
registryCredential = 'dockerhub'
}
stages {
stage('Build') {
steps {
sh 'docker build -t finalprojbackend1 .'
}
}
stage('Test') {
steps {
sh 'docker container rm -f containerbackend1 || true'
sh 'docker container run -p 9005:8080 --name containerbackend1 -d finalprojbackend1'
sh 'sleep 10'
sh 'curl -I http://localhost:9005/hello'
}
}
stage('Publish') {
steps{
//sh 'curl -I http://localhost:9005/hello'
script {
docker.withRegistry( '', registryCredential ) {
sh 'docker login'
sh 'docker tag finalprojbackend1 kamranyaqub1/finalprojbackend1:lblfinalbackend'
sh 'docker push kamranyaqub1/finalprojbackend1:lblfinalbackend'
}
}  
}
}
}
}
