puppet-opendj
=============

`puppet-opendj` configures your ForgeRock OpenDJ servers for use with OpenAM. This assumes tha puppet has been installed using the enterprise RPM package provided by Forgerock ( https://backstage.forgerock.com/#!/downloads/OpenDJ ).

## Usage
In your hieradata file...

Basic usage:
```yaml
---
opendj::admin_password: my_password
opendj::base_dn: dc=example,dc=com
```

With more options:
```yaml
---
opendj::ldap_port: 1389
opendj::ldaps_port: 1636
opendj::admin_port: 4444
opendj::repl_port: 8989
opendj::jmx_port: 1689
opendj::admin_user: cn=My User
opendj::admin_password: my_password
opendj::base_dn: dc=example,dc=com
opendj::home: /opt/opendj
opendj::user: opendj
opendj::group: opendj
opendj::tmpdir: /tmp

# For node-hostname alias in cases when the default fqdn = unwanted-node-name.example.com
opendj::host: ldap-node-alias1.example.com

# For slave
opendj::master: opendj-master-node.example.com

# Overwrite values in ${opendj::home}/config/java.properties
opendj::java_properties:
    start-ds.java-args:
        value: -server -Xms2G -Xmx2G -XX:+UseConcMarkSweepGC -XX:NewSize=512M
    import-ldif.offline.java-args:
        value: -server -Xms1024M -Xmx1024M
    ...
```
