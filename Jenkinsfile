node("docker") {
    docker.withRegistry('hub.docker.com', '942a4ce6-14d2-4daa-a4c4-1109f5e59252') {
    
        git url: "https://github.com/hjnijlunsing/docker-openvpn-armhf", credentialsId: 'dc0077b7-37a0-482f-8254-12cce2dc2563'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "nijlunsing/openvpn-armhf"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}