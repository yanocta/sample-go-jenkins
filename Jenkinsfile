pipeline{
    agent { Dockerfile true }
    environment {
        root = "go"
        branch = "master"
        scmUrl = "https://github.com/yanocta/sample-go-jenkins.git"
    }

    stages {
        stage("Go Version") {
            steps{
                sh "${root} version"
            }
        }

        stage("Git Clone") {
            steps{
                git branch: "${branch}", url: "${scmUrl}"
            }
        }

        stage("Go Test") {
            steps{
                sh "${root} test ./... -cover"
            }
        }

        stage("Go Build") {
            steps{
                sh "${root} build ./..."
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