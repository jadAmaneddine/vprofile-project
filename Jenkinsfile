pipeline {
    agent any
    tools {
        maven "MAVEN3"
        jdk "JDK8"
    }

    environment {
        SNAP_REPO = 'vprofile-snapshot'
        RELEASE_REPO = 'vprofile-release'
        CENTRAL_REPO = 'vpro-maven-central'
        NEXUS_GRP_REPO = 'vpro-maven-group'
        NEXUSIP = '172.31.30.49'
        NEXUSPORT = '8081'
        NEXUS_USER = 'admin'
        NEXUS_PASS = 'admin'
    }

    stages {
        stage('Build') {
            steps {
                sh '''
                    mvn -s settings.xml -DskipTests \
                        -Dnexus.user=${NEXUS_USER} \
                        -Dnexus.pass=${NEXUS_PASS} \
                        -Dnexus.ip=${NEXUSIP} \
                        -Dnexus.port=${NEXUSPORT} \
                        install
                '''
            }
        }
    }
}
