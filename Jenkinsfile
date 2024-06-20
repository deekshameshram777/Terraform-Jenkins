pipeline{
    agent any
    stages{
        stage('Deploy') {
            steps{
                sh "az login"
                echo "Login succeeded"
            }
        }
        
        stage ("Code Clone"){
            steps{
                git url: "https://github.com/deekshameshram777/Terraform-learnings", branch: "main"
                echo "Code Cloned successfully"
            }
        }
        
        stage ("terraform init"){
            steps{
                sh "terraform init"
                echo "Initailaized Backend and Plugins successfully"
            }
        }
        
        stage ("Terraform Validate"){
            steps{
                sh "terraform validate"
                echo "Validated successfully"
            }
        }
        
        stage ("terraform plan"){
            steps{
                sh "terraform plan"
                echo "Plan created successfully"
            }
        }
        
        stage ("terraform apply"){
            steps{
                sh "terraform apply --auto-approve"
                echo "Changes applied successfully"
            }
                
        }
    }
}
