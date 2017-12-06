
// vi skal lave tre stages 
node {
    stage ('Preparation'){
        echo 'Stage preparation'
        echo 'vi kloner fra Git'
        git credentialsId: '6dda151e-9ae5-4118-8547-c51c2ceba009', url: 'git@github.com:zidansken/jenkins-workshop.git'
    }
}
node {
    stage ('Build'){
        echo 'Stage Build'
        echo 'Vi bygger i Maven'
        // vi har allerede pullet imaget fra docker 
        
        //sh 'docker container run -i maven:3-jdk-8 '
        
        sh 'docker container run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn clean package'
    }
}
node {
    stage ('Results'){
        echo 'stage Results'
        junit allowEmptyResults: true, testResults: '**/target/surefire-reports/TEST-*.xml'
        echo 'Vi arkiverer xml-filen'
        archiveArtifacts 'target/surefire-reports/TEST-*.xml'
    }
}

node {
    stage ('Javadoc') {
        echo 'Stage Javadoc'
        //sh 'docker run -i --rm --name my-maven-project -v "$PWD":/usr/src/mymaven -w /usr/src/mymaven maven:3-jdk-8 mvn site'
        //archiveArtifacts 'target/javadoc/*'
        archiveArtifacts 'target/gildedrose-*.jar'
    }
}

