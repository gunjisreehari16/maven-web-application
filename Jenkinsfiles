node{
    
    def mavenHome = tool name: "maven" 
    stage("checkout"){
        git credentialsId: 'gitaccess', url: 'https://github.com/gunjisreehari16/maven-web-application.git'
    }
    stage("Build"){
    
    sh "${mavenHome}/bin/mvn clean package"
    }

    stage("sonarqube"){  
    sh "$mavenHome/bin/mvn sonar:sonar"
    }
    
    stage("Nexus"){  
    sh "$mavenHome/bin/mvn deploy"
    }
    stage("Deploy to tomcat"){
    sshagent(['tomcatcredentails']) {
    sh "scp -o StrictHostkeyChecking=no target/maven-web-application.war ubuntu@44.203.91.142:/opt/tomcat10/webapps"
}
}
    
}
