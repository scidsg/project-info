# Sending Messages

For someone in your community to send you a Hush Line message, they just need to go to one of your addresses. 

## 1. Tor

If you chose a Tor-only deployment you should have seen an output like this after installation completed:

```
✅ Installation complete!

Hush Line is a product by Science & Design.
Learn more about us at https://scidsg.org.
Have feedback? Send us an email at hushline@scidsg.org.

• Hush Line is running
http://5450rww63n5yvp5xzojb41rcx63g3pwaig63ezwp×5x75igzh×4w6qyd…onion
```

Open up Tor Browser and paste your onion address in the addess bar. Tor is a little slower than regular internet, so it'll take a few seconds before your site loads.

![25-tor](https://github.com/scidsg/project-info/assets/28545431/9f7171aa-2c9d-4e43-97fa-e2530dd15a7b)

## 2. Public Websites

If you deployed Hush Line to a public website, you shouldh have seen an output like this:

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

In the example above, the first and the last address can load in regular browsers like Chrome, Firefox, or Safari. The onion-only address needs Tor Browser to load.

The first address should be easy to recognize, but the last might look different. It's called an onion-bound address, and it's a new way of making your onion address discoverable through HTTPS logs. During the installation we requested and configured automatically renewing Let's Encrypt certificates for your domain name. This provides a secure connection from the user's browser to your server. When a certifiate is issued, it's logged in publicly discoverable certificate logs. Now, if someone searches for your domain, they'll see all of the domain names issued a HTTPS certificate. One of them will include your onion address, making it's discovery more resistant to censorship! Learn more at [sauteed-onions.org](sauteed-onions.org).

![40-public-domain](https://github.com/scidsg/project-info/assets/28545431/75ad4f1f-73e5-4d12-91fe-5d5007a63087)
