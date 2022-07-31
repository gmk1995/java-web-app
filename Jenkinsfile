pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                git url: 'https://github.com/gmk1995/java-web-app.git'
            }
        }
        stage('build && SonarQube analysis') {
            steps {
                withSonarQubeEnv('sonarjenkins') {
                    // Optionally use a Maven environment you've configured already
                    withMaven(maven:'MavenBuild') {
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
