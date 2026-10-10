# Laboratorio 3 - Terraform con Azure

Basado en el `main.tf` y `variables.tf` suministrados para el tercer programa.
Crea: Resource Group, Log Analytics Workspace, Application Insights, Linux App Service Plan y Linux Web App.

## Requisitos
- Terraform >= 1.13
- Azure CLI y una suscripcion con permisos para crear recursos
- Iniciar sesion: `az login`
- Ver suscripciones: `az account list -o table`

## Ejecucion desde PowerShell en esta carpeta

```powershell
Copy-Item terraform.tfvars.example terraform.tfvars
notepad terraform.tfvars
az login
az account set --subscription "TU-ID-DE-SUSCRIPCION"
terraform init
terraform fmt
terraform validate
terraform plan -out=lab3.tfplan
terraform apply lab3.tfplan
terraform output
```

Reemplaza el ID de suscripcion y `web_app_name` por un nombre mundialmente unico. El archivo terraform.tfvars no debe subirse a Git.
Si se modifica terraform.tfvars despues del plan, vuelve a ejecutar `terraform plan -out=lab3.tfplan`.
La region `mexicocentral`, SKU `F1` y Node `24-lts` vienen como valores de laboratorio, pero pueden no estar habilitados para tu suscripcion o combinacion de recursos. Si Azure rechaza el despliegue, revisa el error antes de cambiar region/SKU.
`main.tf` usa Linux (no Windows). Azure puede facturar telemetria y otros recursos. Revisa costos y cuotas antes de aplicar.

## Evidencias
Capturas de `terraform init`, `terraform validate`, `terraform plan`, `terraform apply`, `terraform output` y grupo de recursos en Azure.

## Limpieza cuando termine la revision
`terraform destroy` (elimina la infraestructura creada, conservar el estado hasta destruir).
