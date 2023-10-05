node {
    checkout scm

    docker.withRegistry('https://registry.hub.docker.com', 'dockerhubs') {

        def customImage = docker.build("seanghouch/nginx:${env.BUILD_ID}")

        /* Push the container to the custom Registry */
        customImage.push()
    }
}
