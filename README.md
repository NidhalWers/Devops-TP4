# Devops-TP4


Nidhal Teyeb - BDIA

L’objectif du TP est de créer une marchine virtuelle Azure en utilisant Terraform.

##Azure Provider

J'ai créé un fichier producer.tf contenant :
```hcl-terraform
terraform {
  required_providers {
    azurerm = {
      source  = "hashicorp/azurerm"
      version = "=3.0.0"
    }
  }
}

# Configure the Microsoft Azure Provider
provider "azurerm" {
  features {}

  subscription_id = "765266c6-9a23-4638-af32-dd1e32613047"
}
```

### variable
On définie ensuite des variables dans variable.tf pour éviter les duplications 

### data

On crée ensuite un fichier data.tf, contenant les données des ressources déjà créées telles que :
- le ressource groupe
- le réseau virtuel
- le subnet

### Création d'une IP publique

### Création d'une network interface

### SSH Private Key

```hcl-terraform
resource "tls_private_key" "rsa-4096-example" {
  algorithm = "RSA"
  rsa_bits  = 4096
}
```

### Création de la machine virtuelle linux

Enfin j'ai créé ma machine virtuelle (devops-20211018) en utilisant la ressource 'azurerm_linux_virtual_machine' ainsi que les données ssh


### Output

On définit aussi une fichier output.tf afin de récupérer notre addresse IP publique au lieu de passer par le portail azure pour la récupérer


### Run

```shell script
terraform init
```


```shell script
terraform plan
```


```shell script
terraform apply
```


```shell script
terraform output -raw tls_private_key > id_rsa
```

```shell script
sudo chmod 600 id_rsa
```

```shell script
ssh -i id_rsa devops@20.216.143.81 cat /etc/os-release

```





## Bonus : 

### formattage 
Afin de formater le code, j’ai utiliser la commande 


```shell script
terraform fmt
``` 

### Aucune duplication 

J'ai utilisé les data.tf et les variables.tf