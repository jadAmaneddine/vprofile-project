pipeline {
    agent any
    tools {
        maven "MAVEN3"
        jdk "OracleJDK11"
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
        NEXUS_LOGIN = 'nexuslogin'
    }

    stages {
        stage('Build') {
            steps {
                script {
                    // Print relevant environment variables that Maven should use
                    

                    // Run Maven in debug mode (-X)
                    // This will be verbose, but it will show us what Maven is doing.
                    sh 'mvn -s settings.xml -DskipTests install'
                }
            }
        }
    }
}