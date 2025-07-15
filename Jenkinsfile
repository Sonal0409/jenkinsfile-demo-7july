pipeline{
    agent any
    tools{
        maven 'mymaven'
    }
    parameters{
        choice(name: 'ENV', choices: ["Dev","QA"] )
    }
    stages{
        
        stage('Build code for development'){
            when{  // if
                expression{   // condition
                    params.ENV == "Dev"   // user selects Dev at runtime =>  
                    // params.ENV Can be Dev or QA
                }
            }
            steps{
                git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
                sh 'mvn compile'
            }
        }
         stage('Test code in test Environment'){
                when{  // if
                expression{   // condition
                    params.ENV == "QA"   // user selects Dev at runtime =>  
                    // params.ENV Can be Dev or QA
                }
            }
            steps{
                git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
                sh 'mvn test'
            }
        }
    }
    
 
}
