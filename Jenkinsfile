node {
    stage 'Install Bower & Gulp'
    checkout scm
    // Get the nodeJs tool.
    // ** NOTE: This 'NodeJs' maven tool must be configured in the global configuration.
    def nodeHome = tool 'NodeJs'
    env.PATH="${env.PATH}:${nodeHome}/bin"
    sh 'npm install -g bower'
    sh 'npm install -g gulp'

    stage 'Npm Install'
    sh 'npm install'

    stage 'Bower Install'
    sh 'bower install'

    stage 'Gulp Build'
    sh 'gulp build'
}