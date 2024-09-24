# Hush Line Raspberry Pi Prerequisites 

In this section you'll need the following things to get Hush Line ready to install:

1. [Raspberry Pi Imager](#1-raspberry-pi-imager)
2. [Tor Browser](#2-tor-browser)
3. [Gmail](#3-gmail)
4. [Mailvelope](#4-mailvelope)
5. [App Password](#8-create-an-app-password)

## Software Downloads

### 1. Raspberry Pi Imager

Like a Macbook runs MacOS, and a Dell runs Windows, a Raspberry Pi runs Linux, which comes in many different flavors depending on your needs. Since we're using a Raspberry Pi, we'll use Raspberry Pi OS (64-bit), an operating system made just for the Pi. The Imager installs the operating system onto your microSD cardc where we'll set up Hush Line. Download it from https://www.raspberrypi.com/software/.

![1-rpi-imager](https://github.com/scidsg/project-info/assets/28545431/a426639b-a1ce-47eb-859b-c5c6d7ee5f9e)

![2-rpi-imager](https://github.com/scidsg/project-info/assets/28545431/e821ace5-4828-45fc-bf58-75d25444573d)

### 2. Tor Browser

Your Hush Line has the option to only be reachable via the Tor Browser. It's not only the most private but also the easiest to set up and deploy.

![3-tor-browser](https://github.com/scidsg/project-info/assets/28545431/dba5de25-383c-443d-b31e-8e55fc5dd8a1)

### 3. Gmail

We'll use Gmail for its high reliability. If you don't already have an account, create one. It's also not a bad idea to have an email address separate from your personal account.

### 4. Mailvelope

To decrypt Hush Line messages, we'll use Mailvelope, which integrates with Gmail and other compatible email providers, adding PGP functionality.

#### 4.1. Securing Your Browser for Mailvelope

To decrypt messages, Mailvelope uses a private key that is stored locally on your device _and_ the Mailvelope password you will create. 

Before installing the Mailvelope extension on your browser, you should first make sure your browser is up-to-date and secured for this usage:

Mailvelope will store your private key within the browser application you use. To minimize any risk of exposure, it is important to prevent your browser from automatically sending usage statistics and crash reports. Make sure to repeat this procedure whenever you use a new browser. Note that you will need to export your private key first if you change browser or device.

**How to stop your browser from automatically sending usage statistics:**

On Firefox, go to "Preferences" -> "Privacy & Security", then scroll down to find "Firefox Data Collection and Use". Disallow all options in this section (unselected).

On Chrome, go to the upper-right 3-dots menu and select "Settings". In the middle menu, select "Sync and Google services". Find the option "Help improve Chrome's features and performance" and make sure to disable (switch to left) the option "Automatically sends usage statistics and crash reports to Google".

More information about this from Mailvelope: 

"How are private keys protected? Can anyone who has access to my computer also access my private key?"
[https://mailvelope.com/en/faq#keys](https://mailvelope.com/en/faq#keys)

#### 4.2. Installing Mailvelope

Once your browser is secured, you can add the Mailvelope extension here (Firefox): [https://addons.mozilla.org/en-US/firefox/addon/mailvelope/
](https://addons.mozilla.org/en-US/firefox/addon/mailvelope/) 

![4-mailvelope](https://github.com/scidsg/project-info/assets/28545431/eabf6c60-50ca-40ce-b217-30fe0451cda1)

Open the extension in your browser and click "Let's Start."

![5-mailvelope](https://github.com/scidsg/project-info/assets/28545431/dd630fae-ad1e-4b0e-8760-5d3e85707f44)

## Creating Your Keys

### 5. Create your keys

Click on "Generate Keys." Give your key a name, enter your Gmail address, and create a strong password.

![6-mailvelope-setup](https://github.com/scidsg/project-info/assets/28545431/1f12555c-bf2f-4f54-8826-22460384e2cf)

![7-generate-key](https://github.com/scidsg/project-info/assets/28545431/73eb943b-5e0a-4fcd-a159-b2b688b3ab89)

![8-key-created](https://github.com/scidsg/project-info/assets/28545431/c4450938-4ab5-4446-9202-a0c2c148838d)

### 6. Verify your email address

Before using your key, you'll have to verify your email address. Look for a message from `Mailvelope Key Server` in your Gmail inbox.

![9-verify-email](https://github.com/scidsg/project-info/assets/28545431/65e11fb4-9788-4cd2-bfe3-bebed1a1d0a1)

The message is encrypted, and when opened, you'll be prompted for your Mailvelope password to read the email. After entering your password, click the link.

![10-decrypt-message](https://github.com/scidsg/project-info/assets/28545431/6cfc1efa-ddc1-4109-b7ce-72cf996e6441)

### 7. Copy your PGP key

After confirming that your email was verified, click on the supplied URL.

![11-confirmation](https://github.com/scidsg/project-info/assets/28545431/e3a55242-d5f1-47db-947b-f75d6a55809f)

Your PGP Key is in the grey box, beginning with `-----BEGIN PGP PUBLIC KEY BLOCK-----` and ending with `-----END PGP PUBLIC KEY BLOCK-----`. Copy your entire key into a notepad for easy access.

![12-public-key](https://github.com/scidsg/project-info/assets/28545431/6ba01973-8fdc-43e1-83a4-5f9152d77a66)
![13-copy-key](https://github.com/scidsg/project-info/assets/28545431/fe400d7a-8dbd-44e4-b360-4f92839caf83)

## App Password

### 8. Create an app password

Hush Line has a mail server installed to encrypted send messages to your email address. You'll need SMTP information, as well as a password. You should never use your main account password; instead, create app-specific passwords. These are essentially purpose-made for single applications. 

From your Gmail account, click on your avatar to access your account-level options. Select `Manage Google Account`.

![14-profile-menu](https://github.com/scidsg/project-info/assets/28545431/bc6f8df3-313b-404d-8911-5fa66785eccb)

Next, click on the Security tab on the left, then scroll to the bottom of the page to find App Passwords.

![15-security](https://github.com/scidsg/project-info/assets/28545431/21cc352e-dc8d-468c-8e98-affe3a382193)
![16-app-passwords](https://github.com/scidsg/project-info/assets/28545431/ecc35f89-c513-4ac3-8e1e-65504ede406f)

Click on App Passwords, then enter a name, then click Create. A dialog will pop up with your app-specfic password. Copy it to a notepad for easy access.

![17-create-password](https://github.com/scidsg/project-info/assets/28545431/9136b863-f24c-495d-9ffa-32adfe15fa05)
![18-copy-password](https://github.com/scidsg/project-info/assets/28545431/b448db84-78e5-4194-a23e-aa62b8449661)

🎉 Congratulations, you're now ready to install Hush Line!
