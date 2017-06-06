try {
    stage('Preparation') {
        parallel (
            "Verify Node 1": {
                node('oracle_jdk8'){
                    echo 'Verify Node 1 - What is in the folder?'
                    sh 'ls -al'
                    sh 'echo "name: $NODE_NAME lables: $NODE_LABELS"'
                }
            },
            "Verify Node 2": {
                node('oracle_jdk8'){
                    echo 'Verify Node 2 - What is in the folder?'
                    sh 'ls -al'
                    sh 'echo "name: $NODE_NAME lables: $NODE_LABELS"'
                }
            }
        )
    }
    stage('Source Control') {
        node {
            echo 'Source Control - What is in the folder?'
            sh 'ls -al'
            sh 'echo "name: $NODE_NAME lables: $NODE_LABELS"'
        }
    }
    node('oracle_jdk8') {
        stage('Code Analysis') {
            parallel (
                    "Code Style Analysis": {
                        echo 'Code Style Analysis - What is in the folder?'
                        sh 'ls -al'
                        sh 'echo "name: $NODE_NAME lables: $NODE_LABELS"'
                    },
                    "Code Bugs Analysis": {
                        echo 'Code Bugs Analysis - What is in the folder?'
                        sh 'ls -al'
                        sh 'echo "name: $NODE_NAME lables: $NODE_LABELS"'
                    }
            )
        }
        stage('Build') {
            echo 'Build - What is in the folder?'
            sh 'ls -al'
            sh 'echo "name: $NODE_NAME lables: $NODE_LABELS"'
        }
        stage('Test') {
            parallel (
                    "Integration Test": {
                        echo 'Integration Test - What is in the folder?'
                        sh 'ls -al'
                        sh 'echo "name: $NODE_NAME lables: $NODE_LABELS"'
                    },
                    "Smoke Test": {
                        echo 'Smoke Test - What is in the folder?'
                        sh 'ls -al'
                        sh 'echo "name: $NODE_NAME lables: $NODE_LABELS"'
                    },
                    "End To End Test": {
                        echo 'End To End Test - What is in the folder?'
                        sh 'ls -al'
                        sh 'echo "name: $NODE_NAME lables: $NODE_LABELS"'
                    },
                    "User Acceptance": {
                        input "Does the user acceptance test pass? Can we proceed to deploy?"
                    }
            )
        }
    }
    stage('Deploy') {
        node {
            echo 'Deploy - What is in the folder?'
            sh 'ls -al'
            sh 'echo "name: $NODE_NAME lables: $NODE_LABELS"'
        }
    }
} catch (exception) {
    currentBuild.result = "FAILED"
    throw exception
} finally {
    echo 'finally'
}
