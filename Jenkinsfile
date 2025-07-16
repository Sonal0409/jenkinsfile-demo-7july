pipeline{
    agent any
    tools{
        maven 'mymaven'
    }
    parameters{
        choice(name: 'ENV', choices: ["Dev","QA"] )
    }
    stages{
        stage('Build code in your Environment'){
           
            steps{
                script{
                    def mvnCMD = [   // variable 1 storing a key and value
                        Dev: 'compile',
                        QA: 'test'
                        ]
                   def CMD =  mvnCMD[params.ENV]  // variable number 2, storing another variable
                    
                git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
                sh "mvn ${CMD}"  // refering the command from varaible 2
            }
            
            
            }
        }
  
}
}
