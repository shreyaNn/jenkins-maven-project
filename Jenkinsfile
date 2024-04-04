    pipeline {
        agent any
        stages {
            stage('Build') {
                steps {
                    sh 'mvn -f hello-app/pom.xml -B -DskipTests clean package'
                }
                post {
                    success {
                        echo "Now Archiving Artifacts......"
                        archiveArtifacts artifacts: '**/*.war'
                    }
                }
            }

            stage('Tests') {
                steps {
                    sh 'mvn -f hello-app/pom.xml test'
                }
                post {
                    always {
                        junit 'hello-app/target/surefire-reports/*.xml'
                    }
                }
            }
        }
    }