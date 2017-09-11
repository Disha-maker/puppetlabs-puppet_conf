
# puppet_conf

#### Table of Contents

1. [Description](#description)
2. [Setup - The basics of getting started with puppet_conf task](#setup)
    * [Setup requirements](#setup-requirements)
3. [Usage - Configuration options and additional functionality](#usage)
4. [Reference - An under-the-hood peek at what the module is doing and how](#reference)
5. [Limitations - OS compatibility, etc.](#limitations)
6. [Development - Guide for contributing to the module](#development)

## Description

This module provides the puppet_conf task. This allows you to change the configuration options in the puppet.conf file. For example changing the puppet master address. It requires Puppet 5 or bolt installed

## Setup

### Setup Requirements

This module requires either Puppet enterprise or Bolt to function.

## Usage

There are a number of ways to execute the puppet_conf task. The examples below check the status of the httpd puppet_conf. 

VIA PE-console see link_here

Via BOLT more information here LINK
```bolt
bolt task puppet_conf status httpd
```

Via the PE CLI, more information here LINK

```pe
puppet task puppet_conf status httpd
```

## Reference

To get the availible actions and parameters run

```pe
puppet task show puppet_conf
```

```bolt
puppet task show puppet_conf
```

or go to https://forge.puppet.com/puppetlabs/puppet_conf/tasks

For a complete list of optional puppet_conf options https://docs.puppet.com/puppet/latest/types/puppet_conf.html

## Development

Here is a quick how to get up and running 
```
git clone git@github.com:puppetlabs/puppet_conf.git
```
```
bundle install --path .bundle/gems/
```
```
BEAKER_destroy=no PUPPET_INSTALL_TYPE=pe BEAKER_PE_DIR=http://enterprise.delivery.puppetlabs.net/2017.3/ci-ready  BEAKER_PE_VER=2017.3.0-rc8-41-g4981bd3 BEAKER_set=centos7-pooler  bundle exec rspec spec/acceptance
```

This will spit out a vmpooler machine name you can ssh to

```
ssh -i ~/.ssh/id_rsa-acceptance root@<VMPOOLER HOSTNAME FROM ABOVE> 
```

show the status of the openssl puppet_conf (use the actual name of your node)
```
puppet task run puppet_conf --nodes cgx1boldbmbi3vn.delivery.puppetlabs.net action=status puppet_conf=httpd
```

display help for puppet_conf
```
puppet task show puppet_conf
```

show help for the task cli
```
puppet task run --help
```
