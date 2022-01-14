# GSP345 | Automating Infrastructure on Google Cloud with Terraform: Challenge Lab


<div align="center">
    <a href="https://www.cloudskillsboost.google/public_profiles/b6ff4f06-e98a-4362-b579-a33dc8ecdb0f/badges/1640192">
       <img src="https://raw.githubusercontent.com/reshalfahsi/terraform_gcp/master/assets/badges.png" width = 450>
    </a>

</div>


Update: 13 January 2022


## Task 1. Create the configuration files

To start, run the following commands in Cloud Shell Terminal:

```
git clone https://github.com/reshalfahsi/terraform_gcp
cd terraform_gcp
```

Open Cloud Shell Editor and edit every `variables.tf` file in the `terraform_gcp` directory by changing `<PROJECT_ID>`, `<VPC_NAME>` and `<BUCKET_NAME>` in accordance with your current credentials.

Then, run `terraform init` in Cloud Shell Terminal.


## Task 2. Import infrastructure

1. Navigate to Compute Engine > VM Instances. 
2. Click on `tf-instance-1`. 
3. Copy the Instance ID down somewhere to use later. 
4. Repeat process number 1 to 3 for `tf-instance-2`.

To import the `tf-instance-1` and `tf-instance-2`, use the following commands in Cloud Shell Terminal, using the Instance ID you copied down earlier.

```
terraform import module.instances.google_compute_instance.tf-instance-1 <Instance ID - 1>
terraform import module.instances.google_compute_instance.tf-instance-2 <Instance ID - 2>

```

Then, run the following commands in Cloud Shell Terminal:

```
terraform plan
terraform apply
```

Type yes at the dialogue after you run the apply command to accept the state changes.


## Task 3. Configure a remote backend

Open Cloud Shell Editor and edit [`main.tf`]("./main.tf") by uncomment line 25 to 27. Next, run the following commands in Cloud Shell Terminal:

```
terraform init
terraform apply
```

Type yes at the dialogue after you run the apply command to accept the state changes.

Open Cloud Shell Editor and edit [`main.tf`]("./main.tf") by uncomment line 8 to 11. Also edit `<BUCKET_NAME>` with your current credentials.

Run the following command in Cloud Shell Terminal. Type yes at the prompt.

```
terraform init
```

## Task 4. Modify and update infrastructure

Open Cloud Shell Editor and edit [`modules/instance/instances.tf`]("./modules/instance/instances.tf") by uncomment line 4 and 28. Next, comment line 3 and 27. In line 50 and 51 edit `<INSTANCE_NAME>` in accordance with your current credentials. Thus, uncomment line 50 to 65.

Run the following commands in Cloud Shell Terminal. Type yes at the prompt.

```
terraform init
terraform apply
```

## Task 5. Taint and destroy resources

Run the following commands in Cloud Shell Terminal. Type yes at the prompt.

```
terraform taint module.instances.google_compute_instance.<INSTANCE_NAME>
terraform init
terraform apply
```

Change `<INSTANCE_NAME>` in accordance with your current credentials.

Next, comment line 50 to 65. Then, run the following command in Cloud Shell Terminal. Type yes at the prompt.

```
terraform apply
```

## Task 6. Use a module from the Registry

Open Cloud Shell Editor and edit [`main.tf`]("./main.tf") by uncomment line 29 to 52. Run the following commands in Cloud Shell Terminal. Type yes at the prompt.

```
terraform init
terraform apply
```

Open Cloud Shell Editor and edit [`modules/instance/instances.tf`]("./modules/instance/instances.tf") by uncomment line 15, 17, 39 and 41. Next, comment line 14, 16, 38 and 40. Then, run the following commands in Cloud Shell Terminal. Type yes at the prompt.

```
terraform init
terraform apply
```

## Task 7. Configure a firewall

Open Cloud Shell Editor and edit [`main.tf`]("./main.tf") by uncomment line 54 to 64. Next, change `<PROJECT_ID>` and `<VPC_NAME>` in accordance with your current credentials. Then, run the following commands in Cloud Shell Terminal. Type yes at the prompt.

```
terraform init
terraform apply
```

## Credit

- Syed Hassaan Ali's [Gist](https://gist.github.com/Syed-Hassaan/e41a83345832666846ee6be0f69c1f36)
- Aabhusan Maharjan's [Github](https://github.com/Aabhusan/terraform-labs)
