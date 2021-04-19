# acm-ansible-demo
Repository for demo the link between RHACM and Ansible Automation Platforms

## Deploy Ansible Tower and the Ansible Resource Operator

1. Apply the policies
```
$ oc apply -f tower-install/manifests/ansible-tower-policies-subscription.yaml
```

The result of these policies will setup the

* Ansible Resource Operator
* prepare the Ansible Tower Project named tower
* create a PeristentVolumeClaim using the default storage class to support Ansible Tower's database (PostgresSQL).

2. Check the results:

```
$ oc get subs.operators --all-namespaces | grep tower
tower-resource-operator   awx-resource-operator         awx-resource-operator
redhat-operators      release-0.1
```

```
$ oc get pvc -n tower
NAME         STATUS    VOLUME   CAPACITY   ACCESS MODES   STORAGECLASS   AGE
postgresql   Pending                                      gp2            8m39s
```

3. Download the latest Ansible Tower for Openshift release

```
wget -O ansible-tower-openshift-setup-latest.tar.gz https://releases.ansible.com/ansible-tower/setup_openshift/ansible-tower-openshift-setup-latest.tar.gz
tar -xfvz /tmp/ansible-tower-openshift-setup-latest.tar.gz
```

4. Configure the inventory inside of the ansible-tower-openshift-setup-xxx/inventory

```
Example in tower-install/tower-setup/config/inventory
```

5.

