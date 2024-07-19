## Install CLI
- [Installing the cf CLI](https://docs.vmware.com/en/VMware-Tanzu-Application-Service/6.0/tas-for-vms/install-go-cli.html)

## Login

```cmd
cf login -a https://api.sys.xiading-tanzu-tas.azdmss-test.net
```
> Ask for the credential

## Select org and space
PCF is designed for a collection of orgs. Before managing the resource, should go to the target space. We can consider the organization as the team's place to put the resource while space is for a project.

This command set to the asa org  and petclinic space

```cmd
cf target -s petclinic -o asa
```

> The manifest under each sub module is targeting for space `enterprise`, use `cf target -s enterprise -o asa` instead.

## Pre app deployment
This section will prepare the services used by the app
- Service Registry
- Config Server
- MySQL DB

```cmd
cf create-service p.service-registry standard petclinic-service-registry
cf create-service -c '{ "git": { "uri": "https://github.com/azure-samples/spring-petclinic-microservices-config", "label": "master" } }' p.config-server standard petclinic-config-server
```

### REF
- [Config Server document reference](https://docs.vmware.com/en/Spring-Cloud-Services-for-VMware-Tanzu/3.2/spring-cloud-services/GUID-config-server-configuring-with-git.html)

## Post app deployment
By default, apps in PCF cannot call each other internally. Below command add policies to enable the network traffic between apps.

```cmd
cf add-network-policy spring-petclinic-api-gateway spring-petclinic-customers-service --protocol tcp --port 8080
cf add-network-policy spring-petclinic-api-gateway spring-petclinic-vets-service --protocol tcp --port 8080
cf add-network-policy spring-petclinic-api-gateway spring-petclinic-visits-service --protocol tcp --port 8080
```