#!/usr/bin/env groovy

node {
    stage('build') {
        checkout scm

        withCredentials([file(credentialsId: 'maven-settings-windows', variable: 'MAVEN_SETTINGS')]) {
            withEnv(["PATH+MAVEN=${tool 'Maven35'}", "JAVA_HOME=${tool '1.8 Auto'}"]) {
                bat("mvn -B -V -U -s %MAVEN_SETTINGS% -Pjenkins clean deploy -DbuildNumber=${BUILD_NUMBER}")
            }
        }
    }
}
