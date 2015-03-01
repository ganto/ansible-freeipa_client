This role installs [SSSD](https://fedorahosted.org/sssd) and [Certmonger](https://fedorahosted.org/certmonger) and configures them to
be used as clients for a [FreeIPA](http://freeipa.org) server.

**This role is still in development. Use it at your own risk.**


### Documentation ###

1. Add the following minimal configuration to your inventory:

        freeipa_client: True
        freeipa_servers: [ 'auth01.{{ ansible_domain }}' ]
				    
  In this case `auth01` is the hostname of the FreeIPA server.

2. Before applying the role, add the host(s) to your FreeIPA server and copy the Kerberos keytab to the corresponding servers.

  On the server:

        ipa host-add --ip-address=<ip-address> <fqdn-hostname>
        ipa-getkeytab -s <ipa-server> -p host/<fqdn-hostname> -k /tmp/krb5.keytab

  On the client:

       scp <ipa-server>:/tmp/krb5.keytab /etc/krb5.keytab



### Authors and license

`freeipa_client` role was written by:
- Reto Gantenbein | [e-mail](mailto:reto.gantenbein@linuxmonk.ch) | [GitHub](https://github.com/ganto)

License: [GPLv3](https://tldrlegal.com/license/gnu-general-public-license-v3-%28gpl-3%29)

***
