node {
    stage("scm") {
        git url: 'https://github.com/TheGuyWithTheEgo/picalculator'
    }
    stage("test and build") {
        sh "docker build -t thejazzman/picalculator ."
    }
    stage("push") {
        withCredentials([[
            $class: 'UsernamePasswordMultiBinding', 
             credentialsId: 'docker_hub',
             usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD'
        ]]) {
            sh "docker login -u $USERNAME -p $PASSWORD"
            sh "docker push thejazzman/picalculator"
        }
    }
}