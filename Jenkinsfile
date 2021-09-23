pipeline {
    agent any
    tools{
        maven "maven3.8.2"
        jdk "jdk8"
    }

    stages {

	    stage('Artifactory configuration') {
            steps {
                rtServer (
                    id: "artifactory-jfrog-server",
                    url: 'http://18.142.147.184:12000/artifactory',
                    credentialsId: rt_jenkins
                )

		        rtMavenDeployer (
                    id: "MAVEN_DEPLOYER",
                    serverId: "artifactory-jfrog-server",
                    releaseRepo: 'hello_world_repo',
                    snapshotRepo: 'hello_world_repo' 
                )
            }
        }   
    

        stage("Build & Deploy") {
            steps {
                echo "Building..."
                rtMavenRun (
                    tool: 'maven3.8.2', // Tool name from Jenkins configuration
                    pom: 'pom.xml',
                    goals: 'clean install',
                    deployerId: "MAVEN_DEPLOYER"
                )
                echo "deoloyed to artifactory..."
            }
        }

        stage("Test") {
            steps {
            echo "Testing..."
            }
        }

	    stage ('Publish build info') {
            steps {
                rtPublishBuildInfo (
                    serverId: "artifactory-jfrog-server"
                )
            }
        }   
    }
}
