pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Building branch: ${env.BRANCH_NAME}"
                bat 'mvn clean package -DskipTests'
            }
        }

        stage('Branch Specific Logic') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'main') {
                        echo 'Main branch: Production-ready build'
                    } else if (env.BRANCH_NAME.startsWith('feature')) {
                        echo 'Feature branch: Development build'
                    } else if (env.BRANCH_NAME.startsWith('release')) {
                        echo 'Release branch: Pre-release validation'
                    } else {
                        echo 'Other branch'
                    }
                }
            }
        }
    }
}
