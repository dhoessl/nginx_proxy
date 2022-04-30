# nginx_proxy
Role for ansible to manage docker containers

role_nginx:
  vhosts:
    test.dhoessl.de:
      domain: 'test.dhoessl.de'
      proxy:
        port: '15509'
      ssl: true
      ipv6: true
      certificate:
        key: '/etc/letsencrypt/live/dhoessl.de/privkey.pem'
        pub: '/etc/letsencrypt/live/dhoessl.de/fullchain.pem'
      client:
        max_body_size: '512M'
        body_timeout: '180s'
      fastcgi:
        buffer:
          number: '64'
          size: '4K'
        hide_header:
          - 'X-Powered-By'

role_nginx:
  vhosts:
    test.dhoessl.de:
      domain: 'test.dhoessl.de'
      proxy:
        port: '15509'
        version: '1.1'
        default_header: true
        header:
          - field: 'test'
            value: 'test'
      ssl: true
      ipv6: true
      certificate:
        key: '/etc/letsencrypt/live/dhoessl.de/privkey.pem'
        pub: '/etc/letsencrypt/live/dhoessl.de/fullchain.pem'
      protocols: 'TLSv1.3 TLSv1.2'
      ciphers: 'RSA:!EXP:!NULL:+HIGH:+MEDIUM:-LOW'
      client:
        max_body_size: '512M'
        body_timeout: '180s'
      fastcgi:
        buffer:
          number: '64'
          size: '4K'
        hide_header:
          - 'X-Powered-By'
