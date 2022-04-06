node ('') {
    timestamps {
        
            step([$class: 'WsCleanup'])
            stage('Checkout code') {
                checkout scm
            }
           
            stage('Build & Deployment') {
                def k8sImage = docker.image('govndgiri2021/androidapp:latest')
                k8sImage.inside("-u 0:0 --entrypoint=''") {
                    
                    dir("android") {
                          sh 'sudo npm install -g react-native-cli'
                         // sh 'npm install'
                          sh 'npm i -f'
                          sh './gradlew clean'
                          sh "bundle install"
                          sh "fastlane distribute version_code:1000$BUILD_NUMBER store_password:$KEYSTORE_PASSWORD key_alias:$KEYWORD_ALIAS"
                    }
                }
                   
            }
    }
 }
