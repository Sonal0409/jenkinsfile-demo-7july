pipeline{
    agent any // any = current available server where jenkins can run this job
    tools{
        maven 'mymaven'
    }
    
    stages{
        stage('Checkout code'){
            steps{
               git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
            }
        }
        stage('Compile Code'){
            steps{
             sh 'mvn compile'
            }
        }
        stage('Review Code'){
            steps{
                sh 'mvn pmd:pmd'
            }
            post{
                success{
                    recordIssues sourceCodeRetention: 'LAST_BUILD', tools: [pmdParser(pattern: '**/pmd.xml')]
                }
            }
        }
         stage('Test Code'){
            steps{
                sh 'mvn test'
            }
            post{
                success{
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
         stage('package Code'){
            steps{
                sh 'mvn package'
            }
        }
        
    }
    
    
}
