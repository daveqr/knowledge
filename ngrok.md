# Ngrok


[Ngrok](ngrok.com) is a tunneling software that allows you to expose local servers or services behind a firewall or NAT (Network Address Translation) to the public internet. It creates secure tunnels from your local machine to a publicly accessible endpoint.

There is a free tier which allows one domain. However, you can enable multiple ports by modifying the config file found at `~/Library/Application Support/ngrok/ngrok.yml` and using the command `$ ngrok start --all`. (See [ngrok — Expose multiple local host ports to the internet](https://medium.com/@singhgautam7/ngrok-make-full-use-of-free-tier-version-to-expose-your-localhost-to-the-internet-1160e652d794) for details.)

```
authtoken: yourTokenHere
tunnels:
  first:
    addr: 8000
    proto: http    
  second:
    addr: 9000
    proto: http
```    

This gives you two forwarding urls that look like:

```
https://8e5c-149-102-226-226.ngrok-free.app/
```