# NGINX on fedora

```bash
sudo dnf install nginx
```

```bash
cat /etc/nginx/conf.d/default.conf
```

## Start and enable the Nginx service

- Start the Nginx service to run it immediately.

```bash
    sudo systemctl start nginx
```

- Enable the Nginx service to start automatically when the system boots up.

```bash
    sudo systemctl enable nginx
```

Check the status of the service to ensure it is running correctly.

```bash
sudo systemctl status nginx

```

## Configure the firewall

- Open the firewall to allow traffic on the default HTTP and HTTPS ports.

```bash
    sudo firewall-cmd --permanent --add-service=http
    sudo firewall-cmd --permanent --add-service=https
```

Reload the firewall to apply the new rules.

```bash
    sudo firewall-cmd --reload
```
