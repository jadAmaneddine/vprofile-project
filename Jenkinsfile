pipeline {
    agent any
    tools {
        maven "MAVEN3"
        jdk "JDK8"
    }

    environment {
        SNAP_REPO = 'vprofile-snapshot'
        RELEASE_REPO = 'vprofile-release'
        CENTRAL_REPO = 'vpro-maven-central' // This is the ID of your mirror in settings.xml
        NEXUS_GRP_REPO = 'vpro-maven-group'
        NEXUSIP = '172.31.30.49'
        NEXUSPORT = '8081'
        NEXUS_USER = 'admin'
        NEXUS_PASS = 'admin'
    }

    stages {
        stage('Build') {
            steps {
                script {
                    // Print relevant environment variables that Maven should use
                    sh 'echo "NEXUS_USER: $NEXUS_USER"'
                    sh 'echo "NEXUS_PASS: $NEXUS_PASS"'
                    sh 'echo "CENTRAL_REPO: $CENTRAL_REPO"'
                    sh 'echo "NEXUSIP: $NEXUSIP"'
                    sh 'echo "NEXUSPORT: $NEXUSPORT"'
                    sh 'echo "NEXUS_GRP_REPO: $NEXUS_GRP_REPO"'

                    // Run Maven in debug mode (-X)
                    // This will be verbose, but it will show us what Maven is doing.
                    sh 'mvn -X -s settings.xml -DskipTests install'
                }
            }
        }
    }
}