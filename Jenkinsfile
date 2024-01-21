pipeline{
    agent any
    stages{
        stage("build"){
            steps{
                sh "docker stop node-app-container"
                sh "docker rm node-app-container"
                sh "docker image rm node-app-todo"
                sh "docker build . -t node-app-todo"
                echo "contruyendo imagen"
            }
        }
        stage("deploy"){
            steps{
                sh "docker run -d --name node-app-container -p 8000:8000 node-app-todo"
                echo "desplegando contenedor"
            }
        }
    }  
    
}

// pipeline {
//     agent { label "dev-server"}
    
//     stages {
        
//         stage("code"){
//             steps{
//                 git url: "https://github.com/AlejandrVilla/node-todo-cicd.git", branch: "master"
//                 echo 'codigo clonado'
//             }
//         }
//         stage("build and test"){
//             steps{
//                 sh "docker build -t node-app-test-new ."
//                 echo 'imagen construida'
//             }
//         }
//         stage("scan image"){
//             steps{
//                 echo 'escaneando imagen'
//             }
//         }
//         stage("push"){
//             steps{
//                 withCredentials([usernamePassword(credentialsId:"dockerHub",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
//                 sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
//                 sh "docker tag node-app-test-new:latest ${env.dockerHubUser}/node-app-test-new:latest"
//                 sh "docker push ${env.dockerHubUser}/node-app-test-new:latest"
//                 echo 'imagen pusheada'
//                 }
//             }
//         }
//         stage("deploy"){
//             steps{
//                 sh "docker-compose down && docker-compose up -d"
//                 echo 'desplegando'
//             }
//         }
//     }
// }
