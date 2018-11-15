# Software Factory

Software factory is a boilerplate/templating tool, for creating the initial setup for a team
wanting to deploy applications with the tools they wish to use.

## Config File

This would be the main file that would contain your configuration for how you would like to
deploy your application.

### Examples

The below example would create a CI pipeline in Jenkins that would clone our Terraform and Ansible
code. It would then create a pipeline that would create a Java application for you and set a
Prometheus server used for monitoring.

```yml
ci: jenkins
cloud: aws
iaac: terraform
app_type: java
cfg_mgmt: ansible
monitoring: prometheus
credentials: /path/to/credentials
create_ci: true
```

This example is like above but this time would be with different tools.

```yml
ci: circleci
cloud: azure
iaac: ansible
app_type: ruby
cfg_mgmt: puppet
monitoring: zabbix
credentials: /path/to/credentials
create_ci: false
```

The outcomes generated will be fairly generic as it is used as a building block for teams, it
is to be used as a way getting you and your team working quickly. You would then need to add the
specific configuration to make it suitable for your use case.

## Caveats

With some of the CI solutions there would be a slight chicken and egg problem. This would be when
the CI tool we are using is not a SaaS solution as then we would need to build the CI infrastructure
before we can create the building blocks for our software pipeline.

One way around this issue would be using Docker on a users local machine to provision and create the CI
service.