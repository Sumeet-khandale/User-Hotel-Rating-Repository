pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/Sumeet-khandale/User-Hotel-Rating-Repository.git'
        SERVICES = "USER-SERVICE RATING-SERVICE HOTEL-SERVICE CONFIG-SERVER API-GATEWAY SERVICE-REGISTRY"
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo '📦 Cloning repository...'
                git branch: 'master', url: "${REPO_URL}"
            }
        }

        stage('Build All Microservices') {
            steps {
                script {
                    def workspace = pwd()
                    def serviceList = SERVICES.split()

                    for (service in serviceList) {
                        def pomPath = "${workspace}/${service}/pom.xml"

                        // Check if the pom.xml file exists
                        def pomExists = fileExists(pomPath)

                        if (pomExists) {
                            echo "⚙️ Building ${service} using Maven inside Docker..."
                            bat """
                                docker run --rm ^
                                    -v "%cd%:/workspace" ^
                                    -w /workspace/${service} ^
                                    maven:3.9.9-eclipse-temurin-17 ^
                                    mvn clean package -DskipTests
                            """
                        } else {
                            echo "⚠️ Skipping ${service} — No pom.xml found."
                        }
                    }
                }
            }
        }
    }

    post {
        success {
            echo '✅ All microservices built successfully!'
        }
        failure {
            echo '❌ Build failed — check logs above.'
        }
    }
}
