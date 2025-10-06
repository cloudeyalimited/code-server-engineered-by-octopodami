# Code-server Engineered by OCTOPODAMI (CEBO) SSL

You can secure your code-server installation with an SSL certificate by following the instructions below.

+ Login into your domain registrar.
+ Update your domain `A` or `CNAME` record to point to the EC2 Instance IP Address.
+ Access your code-server admin panel at `http://your-instance-ip:8080` and update the domain configuration in your code-server settings. For example, change from `http://your-instance-ip:8080` to `https://mydomainname.com`
+ Wait for 15-20 minutes so DNS can propagate.
+ Login into the EC2 instance via the terminal.
+ Run these commands:

```sh
sudo su -
dnf update -y
amazon-linux-extras install epel -y
dnf install certbot python3-certbot-nginx -y
sudo certbot --nginx
## Answer all the questions (this is a comment)
## Then, specify your domain name (this is a comment)
sudo certbot renew --dry-run
```

+ Update code-server configuration to use HTTPS:

```sh
sudo nano /etc/code-server/config.yaml
```

Find and update these settings:

```yaml
bind-addr: 0.0.0.0:8080
auth: password
password: your-password
cert: /etc/letsencrypt/live/mydomainname.com/fullchain.pem
cert-key: /etc/letsencrypt/live/mydomainname.com/privkey.pem
```

+ Restart code-server:

```sh
sudo systemctl restart code-server@ec2-user
```

+ Access your domain name (`https://mydomainname.com`) in the browser.

## Alternative: Using code-server with Let's Encrypt Directly

If you prefer to configure SSL directly through code-server without nginx:

1. Ensure your domain points to your EC2 instance
2. Install certbot:

   ```sh
   sudo dnf install certbot -y
   ```
3. Stop code-server temporarily:

   ```sh
   sudo systemctl stop code-server@ec2-user
   ```
4. Obtain certificate:

   ```sh
   sudo certbot certonly --standalone -d mydomainname.com
   ```
5. Update code-server configuration:

   ```sh
   sudo nano /etc/code-server/config.yaml
   ```

   Add or update:

   ```yaml
   bind-addr: 0.0.0.0:8080
   auth: password
   password: your-password
   cert: /etc/letsencrypt/live/mydomainname.com/fullchain.pem
   cert-key: /etc/letsencrypt/live/mydomainname.com/privkey.pem
   ```
6. Restart code-server:

   ```sh
   sudo systemctl start code-server@ec2-user
   ```

## Links

1. [Product Website](https://aws.amazon.com/marketplace/pp/prodview-iyn7nuvxxqcjg)
2. [EULA](./octopodamiEULA.txt)
3. [Knowledgebase](https://github.com/cloudeyalimited/code-server-engineered-by-octopodami/-/wikis/home)
4. [Issue Tracking](https://github.com/cloudeyalimited/code-server-engineered-by-octopodami/-/issues)
5. [Changelog](./changelog.md)

## Support

[Email](mailto:tech@cloudeya.org) support is available to Amazon Web Services Marketplace Customers. We do not offer refunds, but you may terminate your Code-server Engineered by OCTOPODAMI (CEBO) Stack at any time.

## License

The documentation is published under [BSD 3-Clause License](license.txt).

## Copyright

(c) 2020 - 2025 [Cloudeya Limited](https://cloudeya.org).