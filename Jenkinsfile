pipeline{
    agent { Dockerfile true }
    environment {
        root = "go"
        branch = "master"
        scmUrl = "https://github.com/yanocta/sample-go-jenkins.git"
    }

    stages {
        stage("Git Clone") {
            steps{
                git branch: "${branch}", url: "${scmUrl}"
            }
        }

        stage("Go Dockerize") {
            steps{
                sh "docker build -t sample-go-jenkins ."
            }
        }

        stage("Deploy") {
            steps{
                echo "DEPLOY SUCCESS"
            }
        }
    }
}


// // Run on an agent where we want to use Go
// node {
//     // Ensure the desired Go version is installed
//     def root = "go"

//     stage 'Checkout'
//     git url: 'https://github.com/yanocta/sample-go-jenkins.git'

//     stage 'preTest'
//     sh "${root} version"

//     stage 'Test'
//     sh "${root} test ./... -cover"

//     stage 'Build'
//     sh "${root} build ./..."
// }