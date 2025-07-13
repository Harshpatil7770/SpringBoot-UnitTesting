pipeline{

agent any 
     
   stages {
       
           stage ('Checkout') {
                 steps {
             
                        echo 'checkout to og repo' 
                        git 'https://github.com/Harshpatil7770/SpringBoot-UnitTesting.git'
                       }
                  } 
       
      
           stage ('Build & Test') {
       
                 steps {

                       echo 'Building Jar and running all the test cases'
                       sh 'mvn clean package -DskipTests=false'
                      } 
      
                 }
 
          stage ('Deploy') {
                steps {
                      echo 'Deploying to dev server'
                     sh ''' 
                     scp target/og.jar ec2-user@3.234.154.193:/app/lib
                      ssh ec2-user@3.234.154.193 'nohup /app/start.sh &'
                      '''
                      echo 'Deployed Succesfully'
                 }
            }
       }
}
