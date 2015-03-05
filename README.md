# Logstash Forwarder
====================

### Description

This is an Ansible role to deploy a 'logstash-forwarder' to any machines that
you want to collect the logs from for your logstash server.  This is to be used
with ELK or Logstash environments.

### Actions

- Installs logstash-forwarder
- Sends Log Files
  - /var/log/auth.log
  - /var/log/syslog
  - /var/log/apache2/other_vhosts_access.log

You can modify the template to include other files: 
`roles/logstash-forwarder/templates/logstash-forwarder.logger.j2`

### Usage

To use this role, just update the default values in:
`roles/logstash-forwarder/defaults/main.yml`

- `logstash_hostname` is the hostname of your logstash server.
- `logstash_port` is the port that your logstash server listens on
- `logstash_ip` is the actual IP address of where your `logstash_hostname`
should point to

You will also need an SSL certificate.  This is due to lumberjack transmitting
over HTTPS.  You should copy it from your logstash server and place it in:
`roles/logstash-forwarder/files/logstash-forwarder.crt`
