# Jenkins Master for Codeontap

This container provides a standard Jenkins install which we recommended for hamlet ( https://codeontap.io ) deployments.
The container also supports deployment using the Hamlet along with using this Jenkins server to deploy other products.

## Environment Variables

### Jenkins Base Level Configuration

- JENKINS_URL
- TIMEZONE
- MAXMEMORY
- JAVA_OPTS
- JAVA_EXTRA_OPTS

### Agent Configuration

This Jenkins instance is designed to work with container based on-demand agents
You can currently use Amazon ECS Agents via the amazon-ecs plugin

- ECS_ARN - The ARN for the ECS cluster to run the task on
- AGENT_JNLP_TUNNEL - An alternate hostname:port combination which can be used to provide a new network path to the JNLP endpoint
- AGENT_JENKINS_URL - An alternate Url which can be used to provide a new network path to the JNLP endpoint
- AGENT_REMOTE_FS - The path on the agent which will be used as the agent users home

Multiple agent labels with their own task definitions are supported

- ECS_AGENT_PREFIX - Sets the prefix used to search in environment variables for the agents

Agents can then be defined using the following syntax

- <ECS_AGENT_PREFIX>_<Agent_Label>_DEFINITION - ECS Task Definition Id or Arn

### Security Realm

The Security realm defines the authentication service provider you would like to use for your Jenkins Instance

- JENKINSENV_SECURITYREALM

### Security Realm - Local

- JENKINSENV_USER
- JENKINSENV_PASS

### Security Realm - Github Auth

- GITHUBAUTH_CLIENTID
- GITHUBAUTH_ADMIN
- GITHUBAUTH_SECRET

### Security Realm - SAML

- SAMLAUTH_META_XML
- SAMLAUTH_META_URL
- SAMLAUTH_META_UPDATE
- SAMLAUTH_ATTR_DISPLAYNAME
- SAMLAUTH_ATTR_USERNAME
- SAMLAUTH_ATTR_GROUP
- SAMLAUTH_ATTR_EMAIL
- SAMLAUTH_LOGOUT_URL
- SAMLAUTH_LIFETIME_MAX
- SAMLAUTH_BINDING
- SAMLAUTH_USERCASE

### Jenkins Credentails

- JENKINSENV_CREDENTIALS_<NAME>_USER
- JENKINSENV_CREDENTIALS_<NAME>_PASSWORD
- JENKINSENV_CREDENTIALS_<NAME>_DESCRIPTION
