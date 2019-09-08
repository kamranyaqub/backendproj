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
////sh 'docker container rm -f node'
sh 'docker container run -p 9005:8080 --name containerbackend1 -d kamranyaqub1/prj1/finalprojbackend'
//sh 'curl -I http://localhost:9005/hello'
}
}
stage('Publish') {
steps{
//sh 'curl -I http://localhost:9005/hello'
script {
docker.withRegistry( '', registryCredential ) {
sh 'docker login'
//sh 'docker tag finalprojbackend kamranyaqub1/prj1/finalprojbackend'
sh 'docker push kamranyaqub1/prj1/finalprojbackend'
}
}  
}
}
}
}
