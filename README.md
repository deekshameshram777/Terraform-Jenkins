# Terraform-Jenkins
# Resource-provisioning-using-Terraform-and-Jenkins
This repository provides an example setup to automate the provisioning of Azure resources using Terraform and Jenkins. This setup demonstrates how to use Infrastructure as Code (IaC) principles to manage Azure infrastructure and automate the deployment process using Jenkins pipelines.

# Prerequisites
Before you begin, ensure you have the following installed/configured on your Linux machine:

**Azure Subscription:** You'll need an active Azure subscription.

**Terraform:** Install Terraform locally on your Linux machine.

**Jenkins:** Install Jenkins on your Linux machine with the necessary Azure and Terraform integration plugins.

**Azure CLI:** Install Azure CLI to interact with Azure from the command line.

# Jenkins Pipeline (Jenkinsfile) -
```
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
```
# Stage Jenkins View -
![image](https://github.com/deekshameshram777/Terraform-Jenkins/assets/156531844/c28ee5e2-f664-4a28-adfa-f093608d7f33)


