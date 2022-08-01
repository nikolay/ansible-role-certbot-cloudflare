# Certbot Cloudflare

Use Cloudflare DNS for wildcard Certbot generation

## Requirements

- Cloudflare DNS setup
- Cloudflare API Key
- Wildcard domain setup (for wildcard certs) [*.domain.com or *.subdomain.domain.com]

## Role Variables

    certbot_cloudflare_email: "cloudflare@example.com"

Your Cloudflare email address

    certbot_cloudflare_api_key: ''

Your Cloudflare Global API Key, optionally encrypted `ansible-vault encrypt_string 'CLOUDFLARE_API_KEY' --name 'certbot_cloudflare_api_key'`

    certbot_certs:
      - email: "{{ certbot_cloudflare_email }}"
      - domains:
          - "*.example3.com"

The wildcard domain to create the cert for. For non-wildcard domains, I recommend using [geerlingguy.certbot](https://github.com/geerlingguy/ansible-role-certbot):

    certbot_cloudflare_acme_server: "{{ certbot_cloudflare_acme_test }}"

or:

    certbot_cloudflare_acme_server: "{{ certbot_cloudflare_acme_live }}"

Let's Encrypt server to use, defaults to test.

## Dependencies

- geerlingguy.pip
- geerlingguy.certbot

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers

      vars:
        certbot_cloudflare_email: "cloudflare@example.com"
        certbot_cloudflare_api_key: 'CLOUDFLARE_API_KEY'
        certbot_certs:
          - email: "{{ certbot_cloudflare_email }}"
          - domains:
              - "*.example3.com"

      roles:
         - nikolay.certbot_cloudflare

## License

MIT / BSD

## Author Information

This role was created in 2018 by [Michael Porter](https://www.michaelpporter.com/), and continued in 2022 by [Nikolay Kolev](https://nikolay.com).
