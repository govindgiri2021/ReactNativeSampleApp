
node ('') {
    timestamps {
        //def err = null
        //try {
            //notifyBuild('STARTED')
            step([$class: 'WsCleanup'])
           
            stage('Build & Deployment') {
                def k8sImage = docker.image('govindgiri2021/android:latest')
                k8sImage.inside("-u 0:0 --entrypoint=''") {
                    sh 'apt-get update && apt-get -y install sudo'
                    sh "javac -version"
                    //adding credentials to the docker image..
                    }
                    dir("android") {
                        //sh 'export PATH=$PATH:/usr/lib/jvm/java-11-openjdk-amd64.'
                        //sh "export JAVA_HOME=${JAVA_HOME}"
                        sh 'sudo npm uninstall -g nativescript'
                        sh 'sudo npm i -g nativescript'
                        sh 'sudo npm i tns-core-modules@latest --save'
                        //sh 'sudo npm install'
                        sh 'sudo npm install npm@latest -g'
                        sh 'sudo npm i -g npm@8.3.1'
                        sh 'sudo npm install --save-dev jetifier'
                        sh 'sudo npx jetify'
                        sh 'sudo npm install -g react-native-cli'
                        sh 'sudo npm install --global yarn --force'
                        sh 'sudo yarn add react-native-cli'
                        sh 'sudo react-native init ReactNativeApp'
                        sh 'cd /var/lib/jenkins/workspace/android_app_test1/android/ReactNativeApp/'
                        sh 'pwd'
                        sh 'ls -al'
                       // sh 'sudo npx react-native start'
                        sh 'sudo npm install'
                       // sh 'sudo react-native run-android'
                        //sh "./gradlew clean"
                        //sh 'echo $JAVA_HOME'
                    }
                    dir("/var/lib/jenkins/workspace/android_app_test1/android/ReactNativeApp") {
                        sh 'pwd'
                        sh 'ls -al'
                       // sh 'sudo npx react-native start'
                        //sh 'sudo npm install'
                        sh 'export ANDROID_HOME=/usr/lib/android-sdk'
                        sh 'export PATH=$ANDROID_HOME/platform-tools:$PATH'
                        sh 'export PATH=$ANDROID_HOME/tools:$PATH'
                       // sh 'sudo ln -s /usr/lib/android-sdk/platform-tools/adb /bin/adb'
                        //sh 'sudo react-native run-android'
                        sh "./gradlew clean"
                        sh 'echo $JAVA_HOME'
                        sh "pwd"
                        //sh 'export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64'
                        sh "bundle install"
                        sh "fastlane distribute version_code:1000$BUILD_NUMBER store_password:$KEYSTORE_PASSWORD key_alias:$KEYWORD_ALIAS"
                    }
                }
            }
        //}
       /*  catch (CaughtErr) {
            currentBuild.result = "FAILED"
            println("Caught exception: " + CaughtErr)
        // error = catchException exception: CaughtErr
        }
        finally {
            println("CurrentBuild result: " + currentBuild.result)
            // Success or failure, always send notifications
            notifyBuild(currentBuild.result)
        } */
   }
