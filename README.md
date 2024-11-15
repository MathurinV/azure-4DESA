Connexion azure:

```bash
az login
```

Lister les groupes de ressources:

```bash
az group list -o tsv
```

Créer un groupe de ressources:

```bash
export GR=PROJET_4DESA
export AZ_LOCATION=francecentral
export AZ_SERVICEBUS_NAMESPACE=sbnamespace91783082
az group create -l $AZ_LOCATION -n $GR
az servicebus namespace create -n $AZ_SERVICEBUS_NAMESPACE --resource-group $GR
az servicebus queue create --name queueName \
--namespace-name $AZ_SERVICEBUS_NAMESPACE \
--resource-group $GR
```

Obtenir la connection string:

```bash
az servicebus namespace authorization-rule keys list --name RootManageSharedAccessKey --namespace-name $AZ_SERVICEBUS_NAMESPACE --resource-group $GR --query primaryConnectionString
```

Supprimer un groupe:

```bash
az group delete --name $GR
```
