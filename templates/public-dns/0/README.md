## Rancher Public DNS

Rancher External DNS service powered by Rancher Public DNS service

#### Usage

- This provider integrates with the rancher-public-dns service to program the DNS records on Rancher's AWS route53 hosted zone 
- To launch this catalog item provide following parameter values:
    - Name  and Description of the Stack where the external-dns provider is launched
    - Rancher Public DNS URL: This is the URL where the rancher-public-dns service is listening
    - TTL
    - Custom DNS Name Template if any ['<service>.<stack>.<environment>.<domain>.' by default]

##### Limitation when running the service on multiple Rancher servers

When running multiple instances of the External DNS service configured to use the same domain name, then only one of them can run in the "Default" environment of a Rancher server instance.

##### Custom DNS name template

By default DNS entries are named `<service>.<stack>.<environment>.<domain>`.    
You can specify a custom name template used to construct the subdomain part (left of the domain/zone name) of the DNS records. The following placeholders are supported:

* `%{{service_name}}`
* `%{{stack_name}}`
* `%{{environment_name}}`

**Example:**

`%{{stack_name}}-%{{service_name}}.statictext`

Make sure to only use characters in static text and separators that your provider allows in DNS names.
