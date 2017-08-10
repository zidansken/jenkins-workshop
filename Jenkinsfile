
node{
        stage('Preparation') {
            git credentialsId: 'sofusalbertsen', url: 'git@github.com:sofusalbertsen/gildedrose.git'
        }
        stage('Build'){
            sh 'mvn clean package'
        }
        stage('Results'){
            junit '**/target/surefire-reports/TEST-*.xml'
        }
    }

