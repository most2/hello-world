pipeline {
    agent any
    tools{

    }

    stages {
        stage("build") {
            when {
                expression {
                    echo 'env.$BRANCH.NAME'
                }
            }
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
