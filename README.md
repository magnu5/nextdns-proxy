# nextdns-proxy

This is a simple DNS server that runs the nextdns-cli package in a debian container.

## Example usage

The docker-compose.yml will work with Balena Cloud.

Add as the Application Environment Variables in the Cloud dashboard:

      NEXTDNS_CONFIG: <<Your NextDNS Config/Endpoint ID here, this can be found on the NextDNS Setup page>
      NEXTDNS_FORWARDING_DOMAIN: <<Your Local DNS Name Here, eg: myfancyhome.net>>
      NEXTDNS_FORWARDING_DNSIP: <<Your Local Router's IP Here, eg: 10.0.1.1>>

