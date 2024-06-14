# Tor-Only Install

A Tor-only install is a great option for someone requiring anonymity and a high level of security, a journalist or human rights activist, for example.

## 1. Run The Installer

After logging in to either your Raspberry Pi or VPS, enter the follow command to start the installation process:

`curl -sSL https://install.hushline.app | bash`

![22-install-hushline](https://github.com/scidsg/project-info/assets/28545431/fa1b19b1-6893-4197-b314-92e44701922b)

Choose "Tor-Only" at the first prompt for the installation type.

![23-tor-only](https://github.com/scidsg/project-info/assets/28545431/89ab37a1-8a55-444d-b414-d03aae739c92)

## 2. Add Email Information

Hush Line will send an email with the encrypted Hush Line message to the account you configure here. Since we're using Gmail, we'll need the following information:

- Gmail address
- SMTP Address: smtp.gmail.com
- App Password (from prerequisites)
- Port: 465
- Public PGP Key (from prerequisites)
  
![23-key](https://github.com/scidsg/project-info/assets/28545431/4c5649d8-940f-4490-b9f3-522ed477e43b)

Once the installation completes, you'll see a message that looks like this:

```
✅ Installation complete!

Hush Line is a product by Science & Design.
Learn more about us at https://scidsg.org.
Have feedback? Send us an email at hushline@scidsg.org.

• Hush Line is running
http://5450rww63n5yvp5xzojb41rcx63g3pwaig63ezwp×5x75igzh×4w6qyd…onion
```

![24-finished](https://github.com/scidsg/project-info/assets/28545431/63625c47-a4cf-4195-ba6a-3930c4592fbb)

🎉 Congratulations! You've successfully set up your own anonymous tip line! 
