# Tor + Public Web Install

If you're someone using Hush Line for non-life-threatening scenarios - educators running a Hush Line for student reporting, or an employer for anonymous employee reporting - you might want to deploy to a public URL - one that will work in browsers like Chrome, Firefox, or Safari. We'll exclusively use a VPS. 

## 1. Run The Installer

After logging in to either your Raspberry Pi or VPS, enter the follow command to start the installation process:

`curl -sSL https://install.hushline.app | bash`

![34-install](https://github.com/scidsg/project-info/assets/28545431/b5563f02-5a49-42d2-bd7b-3e1cee3b15c6)

Choose "Tor + Public Domain" at the first prompt for the installation type.

![35-public](https://github.com/scidsg/project-info/assets/28545431/299aba44-9636-466d-aa20-7cb4e444cfb6)

## 2. Add Information

Hush Line will send an email with the encrypted Hush Line message to the account you configure here. You'll also need to purchase a domain name for your Hush Line. We'll need the following information:

- Domain name
- Gmail address
- SMTP Address: smtp.gmail.com
- App Password (from prerequisites)
- Port: 465
- Public PGP Key (from prerequisites)

![36-key](https://github.com/scidsg/project-info/assets/28545431/7af7d0e6-0d06-4cbf-8794-263685b43584)

## 3. Configure DNS

Now we need to point your domain name to your new Droplet. When the installer gets to the final step, it will display the exact information that you need to enter in your domain's DNS settings.

![38-dns-settings](https://github.com/scidsg/project-info/assets/28545431/4fd3edbd-b50d-4a42-80c9-d263e2e32944)

Once the installation completes, you'll see a message that looks like this:

```
✅ Installation complete!

Hush Line is a product by Science & Design.
Learn more about us at https://scidsg.org.
Have feedback? Send us an email at hushline@scidsg.org.

● Hush Line is running
https://ourdemo.app
http://jnaoywuss3dbgrmroeoqtsjymzf46in7lzh3bx6nwv3bzvwmhdvqytad.onion
https://jnaoywuss3dbgrmroeoqtsjymzf46in7lzh3bx6nwv3bzvwmhdvqytad.onion.ourdemo.app
```

![39-https-complete-1](https://github.com/scidsg/project-info/assets/28545431/3710b96a-a630-47b2-a88e-07da40c5a4ba)

🎉 Congratulations! You've successfully set up your own public anonymous tip line! 
