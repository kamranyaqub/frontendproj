pipeline {
agent any
environment {
registryCredential = 'dockerhub'
}
stages {
stage('Build') {
steps {
sh 'docker build -t finalprojfrontend1 .'
}
}
stage('Test') {
steps {
////sh 'docker container rm -f node'
sh 'docker container run -p 9006:8080 --name containerfrontend1 -d finalprojfrontend1'
//sh 'curl -I http://localhost:9006/'
}
}
stage('Publish') {
steps{
//sh 'curl -I http://localhost:9006/hello'
script {
docker.withRegistry( '', registryCredential ) {
sh 'docker login'
sh 'docker tag finalprojfrontend1 kamranyaqub1/finalprojfrontend1:lblfinalfrontend'
sh 'docker push kamranyaqub1/finalprojfrontend1:lblfinalfrontend'
}
}  
}
}
}
}
