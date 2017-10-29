# OpenFaaS-AWS

Functioning but Work-in-Progress Ansible Playbook to instantiate a single VM in AWS and deploy OpenFaaS to it.  Currently it does require some configuration via the AWS portal to set up security group (SG) rules, obtain your keypair, etc.  These are typically one time configurations, so once configured the playbook can perform repeat runs without any changes.

Requires Ansible and Boto to be available.  Once available let boto know your account details:

```sh
$ touch ~/.boto
```

Add your credentials to `~/.boto`:

```ini

[Credentials]
AWS_ACCESS_KEY_ID=<YOUR AWS ACCESS KEY>
AWS_SECRET_ACCESS_KEY=<YOUR AWS SECRET ACCESS KEY>

```

Pick a machine size & region, and obtain your SG / subnet / keypair details from the AWS portal and complete `ec2_vars/OpenFaaS.yml` accordingly.

Run the playbook:

```
ansible-playbook -i localhost, -e "type=OpenFaaS" provision-OpenFaaS-ec2.yml
```

