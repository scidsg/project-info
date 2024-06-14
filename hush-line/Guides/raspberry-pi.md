![23-key](https://github.com/scidsg/project-info/assets/28545431/58dec3f5-835e-46fe-b774-0d87bfa05547)# Install Hush Line on a Raspberry Pi

In this section, we'll need the following:

- Raspberry Pi
- microSD Card
- Power Supply

## Prep Your Card

### 1. Raspberry Pi Imager
Open the Raspberry Pi Imager and click `Choose OS > Raspberry Pi OS (other) > Raspberry Pi OS (64-Bit)`.

Insert your microSD card into your computer, and then click `Choose Storage` and select your card.

![19-rpi-imager](https://github.com/scidsg/project-info/assets/28545431/4a05a403-45c8-4a70-be4a-78aac27fea0c)

Before clicking Write, click on the Settings gear in the bottom right of the window. Configure the following settings:

- Hostname = hushline
- Enable SSH with password authentication
- User = Hush
- Set a strong password
- Wifi settings

![20-advanced](https://github.com/scidsg/project-info/assets/28545431/46a822c8-bf5e-40c0-9c45-fcbc19a1c9ad)

## Boot up and log in to Your Pi

### 2. Insert microSD Card

Take your SD card and insert it into your Raspberry Pi. You'll find the SD card slide on the bottom of the board, opposite the ethernet ports.

Plug the power supply into the device and let it boot up.

### 3. Terminal

On a Mac, open Spotlight search by pressing CMD + Space. Enter "Terminal" and select the application with the same name. 

Enter `ssh hush@hushline.local`, and when prompted, enter the password you created in the first step.

![21-terminal-login](https://github.com/scidsg/project-info/assets/28545431/013192bc-3046-40ce-8335-7021d562a64c)

## Install Hush Line

### 4. Start the script

Once logged in, enter `sudo su` then `curl -sSL https://install.hushline.app | bash` to start the installation.

![21-terminal](https://github.com/scidsg/project-info/assets/28545431/e2729634-6ee7-42bd-8736-d10ef1c4896c)
![22-install-hushline](https://github.com/scidsg/project-info/assets/28545431/1c4b9fa3-758f-4305-ad98-335d761ba508)
![23-prompt](https://github.com/scidsg/project-info/assets/28545431/ed5bf0d1-5a0b-4fa8-8bfa-870504dfc271)

### 5. Add your information

The installer will walk you through everything needed to get Hush Line working. We'll need the following information:

- Gmail address
- SMTP address: smtp.gmail.com
- App password (from prerequisites)
- Port: 465
- Public PGP key (from prerequisites)

![23-key](https://github.com/scidsg/project-info/assets/28545431/0a5a1c11-c45b-454b-83d3-932ddf658398)

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

## Send a Message

### 6. Open Tor Browser

Copy your onion address, open Tor Browser, paste it in, and press Enter. In a moment, your Hush Line site will load. Enter a message and click "Submit."

![25-tor](https://github.com/scidsg/project-info/assets/28545431/0ecdc349-464d-4707-bd79-1551ddda3777)

![26-message-submitted](https://github.com/scidsg/project-info/assets/28545431/38dbf8d1-da2f-4620-855c-f76392617d85)

## Read Your Message

### 7. Open Gmail

Back in the Gmail account you configured during the Hush Line installation, look for a message with the subject "🤫 New Hush Line Message Received." When you click on the message you'll briefly see the encrypted contents and may be prompted to enter your Mailvelope password. Your decrypted message will display.

![27-encrypted-message](https://github.com/scidsg/project-info/assets/28545431/a715443d-9843-497b-9200-6d8cd1f1f898)

![28-decrypted-message](https://github.com/scidsg/project-info/assets/28545431/928e6e02-886f-4098-972c-11b30159f399)

## Sharing Your Address

When sharing your address, it's important to let your community know what it is, how to use it, and that you approve it. Trust is the most essential part of hosting a tip line, and ensuring that your community has confidence that you are the owner will go a long way. Send your address in an email blast with instructions, add it to your website, or post it on your social channels. 

🎉 Congratulations! You now have a self-hosted, anonymous tip line! 
