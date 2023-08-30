# Jenkins Declarative Pipeline with Docker


## Task 1

```Groovy
pipeline {
    agent { docker { image 'maven:3.9.3-eclipse-temurin-17-alpine' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
    }
}

```


## Task 2

```Groovy
pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                script {
                    docker.image('maven:3.9.3-eclipse-temurin-17-alpine').inside {
                        sh 'mvn --version'
                    }
                }
            }
        }
    }
}

```
