node {
    def app
    stage('Clone repository') {
       git 'https://github.com/jaeyoo-ni/open_prac.git'
    }
    stage('Build image') {
       app = docker.build("jycho98/test")
    }
    stage('Test image') {
       app.inside {
           sh 'make test'
       }
    }
    stage('Push image') {
       docker.withRegistry('https://registry.hub.docker.com', 'jycho98') {
          app.push("${env.BUILD_NUMBER}")
          app.push("latest")
       }
    }
}

