pipeline {
- agent any
-
- stages {
- stage('Checkout GitHub repo') {
- steps {
- checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ankurroy4git/dockerdemo']])
- }
- }
- stage('Build and Tag Docker Image') {
- steps {
- script {
- sh 'docker build . -t hellodocker'
- sh 'docker tag hellodocker ankurroy4docker/learning'
- }
- }
- } 
- stage('Push the Docker Image to DockerHUb') 
steps {
- script {
- withCredentials([string(credentialsId: 'docker_ankur', variable: 'docker_hub')]) {
   sh 'docker login -u ankur.roy@heritageit.edu -p ${docker_hub}' // some block
}
- sh 'docker push ankurroy4docker/learning'
- }
- }
- }
-
- stage('Deploy deployment and service file') {
- steps {
- script {
-//kubernetesDeploy configs: '', kubeConfig: [path: ''], kubeconfigId: 'kubernet_ankur', secretName: '', ssh: [sshCredentialsId: '*', sshServer: ''], textCredentials: [certificateAuthorityData: '', clientCertificateData: '', clientKeyData: '', serverUrl: 'https://'] 


kubernetesDeploy configs: 'deploymentsvc.yaml', kubeconfigId: 'k8_auth'
- }
- }
- } 
- } 