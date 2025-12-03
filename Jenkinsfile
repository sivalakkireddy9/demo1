pipeline {
    agent any
          stages {
              stage('clone project') {
                                    steps {
                      git branch:'master',
                      url:'https://github.com/sivalakkireddy9/demo1'                                    
                                             }
                                    }
              stage('clean') {
                               steps {
                                    sh 'mvn clean'
                                    }
                            }

               stage('compile') {
                            steps {
                                 sh 'mvn compile'
                                 }
                               }

                stage('test') {
                               steps {
                                  sh 'mvn test'
                                    }
                            }

                stage('build') {
                                steps {
                                    sh 'mvn clean install'
                                    }
                            }
          }        
        post {
        success {
            emailext(
                subject: "Build Success: ${currentBuild.fullDisplayName}",
                body: "The build ${env.BUILD_URL} was successful!",
                to: "sivalakkireddy999@gmail.com"
            )
        }
        failure {
            emailext(
                subject: "Build Failed: ${currentBuild.fullDisplayName}",
                body: "The build ${env.BUILD_URL} failed. Please check.",
                to: "sivalakkireddy999@gmail.com"
            )
        }
     }
   }
