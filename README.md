<hr>

# HyperXN - The Most Reliable Open-Source Pterodactyl Dashboard! (v1)

All features:
- Resource Management (Use it to create servers, etc)
- Coins (AFK Page earning, Linkvertise earning, Gift them away) (BETA)
- Renewal (Require coins for renewal)
- Coupons (Gives resources & coins to a user)
- Servers (create, view, edit servers)
- Login Queue (prevent overload)
- User System (auth, regen password, etc)
- Store (buy resources with coins)
- Dashboard (view resources)
- Admin (set/add/remove coins & resources, create/revoke coupons)
- API (for bots & other things)
- & Much More Coming Soon in future!
  
# Note:

You must keep **Powered by HyperXN** in the footer in order to use the dashboard!

<hr>

# Installation Guide

Warning: You must have Pterodactyl Game Panel already setuped along with a domain!
1. Upload the file above onto a Pterodactyl NodeJS server [Download the egg from Parkervcp's GitHub Repository](https://github.com/parkervcp/eggs/tree/master/bots/discord/discord.js)
2. Unarchive the file and set the server to use NodeJS 16
3. Configure settings.json (specifically panel domain/apikey and discord auth settings for it to HyperXN work!)
4. Start the server (Ignore the 2 strange errors that sometimes come up!)
5. Login to your DNS manager (Such as Cloudflare), point the domain you want your dashboard to be hosted on to your VPS IP address. (For Example: dash.hyperxn.xyz 192.168.0.2)
6. Run `apt install nginx && apt install certbot` on the vps!
7. Run `ufw allow 80` and `ufw allow 443` on the vps!
8. Run `certbot certonly -d <Your HyperXN Domain>` then do 1 and put your email
9. Run `nano /etc/nginx/sites-enabled/hyperxnv1.conf`
10. Paste the configuration at the bottom of this and replace with the IP of the pterodactyl server including the port and with the domain you want your dashboard to be hosted on.
11. Run `systemctl restart nginx` and try open your domain.

# Nginx Proxy Config
```Nginx
server {
    listen 80;
    server_name <domain>;
    return 301 https://$server_name$request_uri;
}
server {
    listen 443 ssl http2;
location /afkwspath {
  proxy_http_version 1.1;
  proxy_set_header Upgrade $http_upgrade;
  proxy_set_header Connection "upgrade";
  proxy_pass "http://localhost:<port>/afkwspath";
}
    
    server_name <domain>;
ssl_certificate /etc/letsencrypt/live/<domain>/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/<domain>/privkey.pem;
    ssl_session_cache shared:SSL:10m;
    ssl_protocols SSLv3 TLSv1 TLSv1.1 TLSv1.2;
    ssl_ciphers  HIGH:!aNULL:!MD5;
    ssl_prefer_server_ciphers on;
location / {
      proxy_pass http://localhost:<port>/;
      proxy_buffering off;
      proxy_set_header X-Real-IP $remote_addr;
  }
}
```

<hr>

### THIS IS A FORK OF HELIACTYL. (A Client which is dead and is the worst) | This was never planned to be released and won't work. This is just a joke! DO NOT waste your time trying installing it. It won't install and instead will show 1,000 of errors! Thank You and have a nice day!

Best,
<br>
Gracesk.


