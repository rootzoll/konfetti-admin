node {
    def imageName = 'konfetti/admin'

    // branches to build docker image and publish
    def branch = env.BRANCH_NAME
    def develop = 'develop'
    def production = 'master'
    def dockerBranches = [develop, production]

    stage 'Install Bower & Gulp'
    checkout scm
    // Get the nodeJs tool.
    // ** NOTE: This 'NodeJs' maven tool must be configured in the global configuration.
    def nodeHome = tool 'NodeJs'
    env.PATH="${env.PATH}:${nodeHome}/bin"
    sh 'npm install gulp'

    stage 'Npm Install'
    sh 'npm install'

    stage 'Bower Install'
    sh 'bower install'

    stage 'Gulp Build'
    sh 'gulp build'

    echo "Git Branch : ${branch}"
    if (dockerBranches.contains(branch)) {
        echo "Building docker container for branch: ${branch}"

        docker.withRegistry('https://docker.io', 'docker-credentials') {

            def dockerImg;
            // ========================================================================
            stage 'Build Docker image'
            // ========================================================================
            echo "build image : ${imageName}:latest"
            dockerImg = docker.build("${imageName}:latest")

            // ========================================================================
            stage 'Tag and push image'
            // ========================================================================
            echo "tag image"
            dockerImg.tag()
            echo "push image"
            dockerImg.push()

            if (production.equals(branch)) {
                stage "Deploy On Production"
                build job: 'DeployKonfettiOnProduction', wait: false
            }
        }
    }
}