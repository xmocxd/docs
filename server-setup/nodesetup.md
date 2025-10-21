# init / install steps
`apt install nodejs`
`apt install npm`
`npm install pm2@latest -g` - install node process manager
`pm2 startup systemd` - configure pm2 startup script for systemd
pm2 can now be controlled via systemctl like `systemctl start pm2-root`

# pm2
`pm2 monit` - monitor
`pm2 list` - list managed apps
`pm2 start xyz.js` - start node app

# nginx setup

edit `/etc/nginx/sites-available/default`
inside `location /` block, add config:

```
    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
```

test config and restart:
`nginx -t` - test config file syntax
`systemctl reload nginx` - reload config
`systemctl restart nginx`

node app will now be at http://ip (not :3000)
