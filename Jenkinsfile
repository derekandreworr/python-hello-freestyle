node ('docker') {
    checkout scm
    
    stage('Build image') {
        def customImage = docker.build("demouser/newappimage:${BUILD_NUMBER}")
    }

    stage('Scan image with Aqua') {
        aqua locationType: 'local', localImage: 'demouser/newappimage:${BUILD_NUMBER}', hideBase: false,  notCompliesCmd: '', onDisallowed: 'fail', showNegligible: false
    }

    stage('Push to registry') {
        // Going to skip this part for testing.
    }

    stage('Scan image with Aqua') {
        aqua locationType: 'local', localImage: 'demouser/newappimage:${BUILD_NUMBER}', hideBase: false,  notCompliesCmd: '', onDisallowed: 'fail', showNegligible: false, register: true, registry: "Docker Hub"
    }


}
