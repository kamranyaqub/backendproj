pipeline {
agent any
environment {
registryCredential = 'dockerhub'
}
stages {
stage('Build') {
steps {
sh 'docker build -t kamranyaqub1/prj1/finalprojbackend .'
}
}
stage('Test') {
steps {
//sh 'docker container rm -f node'
sh 'docker container run -p 9005:8080 --name containerbackend -d kamranyaqub1/prj1/finalprojbackend'
sh 'curl -I http://localhost:9005'
}
}
stage('Publish') {
steps{
script {
docker.withRegistry( '', registryCredential ) {
sh 'docker push kamranyaqub1/prj1/finalprojbackend'
}
}
}
}
}
}
