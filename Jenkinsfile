pipeline {
    agent any
    tools{
        maven "maven3.8.2"
        jdk "jdk8"
    }

    stages {
        stage("build") {
            steps {
            echo "Building..."
            }
        }

        stage("Test") {
            steps {
            echo "Testing..."
            }
        }

        stage("Deploy") {
            steps {
            echo "create tag..."
            echo "deoloying to artifactory..."
            }
        }
    }



}
