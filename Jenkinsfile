pipeline {
agent any
environment {
registryCredential = 'dockerhub'
}
stages {
stage('Build') {
steps {
sh 'sudo docker build -t kamranyaqub1/finalprojbackend .'
}
}
stage('Test') {
steps {
//sh 'docker container rm -f node'
sh 'sudo docker container run -p 9003:8080 --name node -d kamranyaqub1/finalprojbackend'
sh 'curl -I http://localhost:9003'
}
}
stage('Publish') {
steps{
script {
docker.withRegistry( '', registryCredential ) {
sh 'sudo docker push kamranyaqub1/finalprojbackend'
}
}
}
}
}
}
