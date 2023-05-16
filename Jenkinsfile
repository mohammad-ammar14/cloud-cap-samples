pipeline {
    agent any
    stages {
        stage('tool info') {
            steps {
                // sh 'sudo apt-get install pack-cli'
                sh 'pack version'
                sh 'pack report'
            }
        }
        stage ('install cds') {
            steps {
                sh 'sudo npm add -g @sap/cds-dk'
            }
        }
        stage('configure pack') {
            steps {
                sh 'cd bookshop'
                sh 'cds build --production'
            }
        }
        stage('build info') {
            steps {
                sh 'pack build bookshop-approuter --path app --buildpack gcr.io/paketo-buildpacks/nodejs --builder paketobuildpacks/builder:base --env BP_NODE_RUN_SCRIPTS='
            }
        }
    }
}
