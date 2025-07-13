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
                      scp /target/og.jar hpatil@ip:/app/lib
                      ssh hpatil@ip 'nohup /app/start.sh &'
                      echo 'Deployed Succesfully'
                 }
            }
       }
}
