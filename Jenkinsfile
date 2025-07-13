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
                     scp target/og.jar ec2-user@44.201.5.177:/app/lib
                      ssh ec2-user@44.201.5.177 'nohup /app/start.sh &'
                      '''
                      echo 'Deployed Succesfully'
                 }
            }
       }
}
