# Terraform EC2 Basic Assignment (AWS)

## 📌 Objective

Learn Terraform basics including initialization, planning, and applying infrastructure by creating an AWS EC2 instance using Infrastructure as Code (IaC).

---

## 🛠️ Tools Used

* Terraform
* AWS CLI
* Amazon Web Services

---

## 📁 Project Structure

```
terraform-ec2-basic/
│── main.tf
│── README.md
```

---

## ⚙️ Prerequisites

1. Install Terraform
2. Install AWS CLI
3. Create an AWS account
4. Configure AWS credentials

---

## 🔐 AWS Configuration

Run the following command:

```
aws configure
```

Enter:

* AWS Access Key
* AWS Secret Key
* Region: `ap-south-1`
* Output format: `json`

---

## 🧱 Terraform Configuration

Create a file named `main.tf` and add the following:

```hcl
provider "aws" {
  region = "ap-south-1"
}

resource "aws_instance" "my_instance" {
  ami           = "ami-0f58b397bc5c1f2e8"
  instance_type = "t3.micro"

  tags = {
    Name = "Terraform-Student-Instance"
  }
}

output "instance_public_ip" {
  value = aws_instance.my_instance.public_ip
}
```

> ⚠️ Note: `t3.micro` is used instead of `t2.micro` because `t2.micro` may not be free-tier eligible in some regions like `ap-south-1`.

---

## 🚀 Steps to Run Terraform

### 1. Initialize Terraform

```
terraform init
```

### 2. Preview Execution Plan

```
terraform plan
```

### 3. Apply Configuration

```
terraform apply
```

Type `yes` when prompted.

---

## 📤 Output

After successful execution, Terraform will display the **public IP address** of the EC2 instance.

Example:

```
instance_public_ip = "xx.xx.xx.xx"
```

---

## ✅ Verification

1. Go to AWS Console
2. Navigate to EC2 Dashboard
3. Check:

   * Instance is running
   * Name: `Terraform-Student-Instance`

---

## 🧹 Cleanup (Important)

To avoid unnecessary charges, destroy resources:

```
terraform destroy
```

Type `yes` when prompted.

---

## 📌 Key Learnings

* Infrastructure as Code using Terraform
* AWS provider configuration
* EC2 instance provisioning
* Terraform workflow: init → plan → apply → destroy

---

-- Nabajyoti Kalita
