# CREATION DES OUTPUTS

Lorsque l’on gère une infrastructure avec terraform, il est intéressant d’utiliser les outputs pour obtenir facilement et rapidement des informations utiles de cette infrastructure.

En effet, les outputs s’affichent systématiquement à la fin de chaque exécution de la commande terraform apply, même si aucune action n’est réalisée.

## Déclaration des outputs

En vous appuyant sur la [documentation officielle de terraform](https://developer.hashicorp.com/terraform/language/values/outputs), déclarez les outputs suivants dans un fichier nommé outputs.tf :

- Le nom du VPC dans lequel se trouve votre infrastructure
- Le nom de votre load-balancer
- Le nom DNS de votre load-balancer
- Le nom du security group de votre load balancer
- Le nom de votre EC2
- L’adresse IP publique de votre EC2
- L’adresse IP privée de votre EC2
- Le nom du security group de votre EC2
- Le nom de votre base de données
- Le endpoint de votre base de données
- Le port utilisé par votre base de données
- Le nom du security group de votre base de données

Les valeurs de vos outputs devront être renseignées via les outputs de vos ressources correspondantes (cf. [aws_lb](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/lb), [aws_instance](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/instance) et [aws_db_instance](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/db_instance)).

## Exécution du code terraform

Exécutez la commande **terraform fmt**, puis la commande **terraform plan -var-file="developpement.tfvars"**. Observez que terraform ne prévoir aucune action sur vos ressources, et que le message **Changes to Outputs** apparaît avec la liste des outputs au-dessous.

Exécutez ensuite la commande **terraform apply -auto-approve -var-file="developpement.tfvars"** et notez que les outputs déclarés dans votre fichier outputs.tf s’affichent.

Terraform affiche les outputs du code à chaque exécution.