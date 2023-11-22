**👷 DRAFT**

<h1 "width:70%">Hush Line: A User-Friendly Approach to Confidential Tip&nbsp;Lines</h1>
Glenn Sorrentino, Executive Director, [Science & Design, Inc.](https://scidsg.org)

## Keywords
Tipline, Tor, onion site, PGP, SMTP, HTTPS, Let's Encrypt, automation, open-source

## Abstract
Many tip lines can be prohibitively complex, requiring expert consultant services, purchasing and managing special infrastructure, or a lengthy setup process. Technical requirements impact end users, who often need to download, learn, and manage a new platform. We built Hush Line to make it easy for organizations or individuals to deploy an anonymous tip line to a public domain or onion-only instance [^1]. The install process fully configures the tip line to automatically update its software, renew HTTPS certificates, and deliver encrypted messages to the owner's email address. Hush Line is a no-maintenance tip line that meets the user where they are without requiring you to manage yet another app. The app is free and open-source, licensed as AGPL 3.0 [^2][^3].

<img src="https://raw.githubusercontent.com/scidsg/project-info/main/hush-line/2.%20Design/device-group.png" width="75%" style="margin:2rem 0;">

## Table of Contents
# Hush Line: A User-Friendly Approach to Confidential Tip Lines

By Glenn Sorrentino, Executive Director, [Science & Design, Inc.](https://scidsg.org)

## Keywords
Tipline, Tor, onion site, PGP, SMTP, HTTPS, Let's Encrypt, automation, open-source

## Abstract
Many tip lines can be prohibitively complex, requiring expert consultant services, purchasing and managing special infrastructure, or a lengthy setup process. Technical requirements impact end users, who often need to download, learn, and manage a new platform. We built Hush Line to make it easy for organizations or individuals to deploy an anonymous tip line to a public domain or onion-only instance [^1]. The install process fully configures the tip line to automatically update its software, renew HTTPS certificates, and deliver encrypted messages to the owner's email address. Hush Line is a no-maintenance tip line that meets the user where they are without requiring you to manage yet another app. The app is free and open-source, licensed as AGPL 3.0 [^2][^3].

## Table of Contents
- [Keywords](#keywords)
- [Abstract](#abstract)
1. [Introduction](#1-introduction)
2. [Problems We're Solving](#2-problems-were-solving)
   - [Users and Use Cases](#21-users-and-use-cases)
     - [Users](#211-users)
     - [Use Cases](#212-use-cases)
3. [System Requirements](#3-system-requirements)
   - [Processor and Cryptography](#31-processor-and-cryptography)
   - [Hardware Requirements](#32-hardware-requirements)
   - [Security and Privacy](#33-security-and-privacy)
4. [Hush Line: The People's Tip Line](#4-hush-line-the-peoples-tip-line)
   - [Goals](#41-goals)
   - [Threat Model and Scope](#42-threat-model-and-scope)
   - [System Architecture](#43-system-architecture)
   - [Application](#44-application)
     - [Encryption](#441-encryption)
       - [Client vs. Server-Side Encryption](#4411-client-vs-server-side-encryption)
       - [Pretty Good Privacy](#4412-pretty-good-privacy)
     - [Email Delivery](#442-email-delivery)
       - [Simple Mail Transfer Protocol](#4421-simple-mail-transfer-protocol)
     - [Hush Line Service](#443-hush-line-service)
     - [Logging](#444-logging)
     - [Censorship Resistance with Sauteed Onions](#445-censorship-resistance-with-sauteed-onions)
5. [Personal Server](#5-personal-server)
   - [Threat Model](#51-threat-model)
   - [Hardware](#52-hardware)
   - [Physical Security](#53-physical-security)
   - [Setup](#54-setup)
6. [Research](#6-research)
   - [Interview Guides](#61-interview-guides)
   - [Asynchronous Surveys](#62-asynchronous-surveys)
   - [Direct Communication with Users and Organizations](#63-direct-communication-with-users-and-organizations)
7. [Auditing Hush Line](#7-auditing-hush-line)
   - [Accessibility](#71-accessibility)
   - [Security](#72-security)
8. [External Collaboration](#8-external-collaboration)
   - [Content Design](#81-content-design)
   - [Visual Design](#82-visual-design)
9. [Documentation](#9-documentation)
10. [Support Model](#10-support-model)
11. [Challenges](#11-challenges)
    - [Financial Support](#111-financial-support)
12. [Future Work](#12-future-work)
    - [Personal Server](#121-personal-server)
    - [Hosted Service](#122-hosted-service)
      - [Risks](#1221-risks)
13. [Hush Line Contributors](#13-hush-line-contributors)
- [References](#references)

## 1. Introduction
Tip lines provide the owner a safe way to receive confidential messages from their community - journalists and the public, educators and students, employers and employees. Tools that exist in this space include SecureDrop, GlobalLeaks, or adapted solutions like running Signal on a spare smartphone [^4][^5][^6]. "I always forget to check Signal on my old phone and feel bad when I remember because someone might actually send something," shared a journalist from Consumer Reports. Another journalist in the EU said, "My favorite thing about SecureDrop is that it's so complicated that people can't install it; I created a consulting business as a result!"

Hush Line attempts to address the obstacles presented by users with less technical proficiency who might need a tip line but don't possess the familiarity required for a technical setup process [^7]. We also resolve the problem of having a spare device that might go unchecked for extended periods. Hush Line installs in just a few minutes, provides a fully guided configuration process, and doesn't require owners to log in to or check on the device since the messages submitted are delivered using SMTP to the email address they set up, ensuring a tip doesn't go unseen. 

Other tip lines are available to end-users as Tor-only options. While this provides additional safeguards for privacy, it also adds complex steps for end-users to overcome. Hush Line allows the owner to deploy to a public website that configures renewing Let's Encrypt HTTPS certificates while also deploying to a Tor onion service by default [^8][^9]. This allows for an even more significant impact on owners reaching their communities.

## 2. Problems We're Solving
Individuals need safe ways to communicate confidential information without fear of being compromised. Whether the sender or receiver, security, privacy, and usability are critical in establishing trust when handling confidential information.

Journalists and newsrooms depend on confidential communications. Geneva Overholder, a contributor to the New York Times, says, "to journalism, sources are the lifeblood of newsgathering [^10]." Whistleblowers risk their personal and professional reputations to expose wrongdoing, and the risks they face include imprisonment and exile. Even the families of journalists and whistleblowers have faced harassment or even detainment [^11]. With such stakes, sources need confidence that they won't be burned.

In the workplace up to 70% of people will either witness or experience workplace harassment or discrimination. Of those people, only 15% will ever make a formal complaint, and fewer than 1 in 100 will find a resolution [^12]. The reason for the stark contrast in reporting is due to fear of retaliation.

In schools, students have entirely different expectations of trust and safety. A 16-year study of one school showed that when they implemented measures in the name of security, including metal detectors, gates, and removing decorative elements from campus, the feeling of safety went down. Peer violence increased, calls to the police quadrupled, and teachers grew increasingly concerned [^13].

### 2.1. Users and Use Cases
#### 2.1.1. Users

- Journalists and newsrooms can use Hush Line to give the public a safe way to leave a confidential tip.
- Employers and board rooms can use Hush Line to build trust by allowing colleagues to leave suggestions or report concerns anonymously.
- Educators and school staff can use Hush Line to host a safe way for students to share information with someone they trust.

#### 2.1.2. Use Cases

- As a journalist, I need to provide sources with a trustworthy way to send information, so they have confidence that the methods will protect their privacy.
- As an educator, I need to provide students with a safe way to share information with school staff they trust, so critical information can be received while protecting the student's identity.
- As an employee that has witnessed workplace abuse, I need a secure and private way to share information with company executives, so that my identity is kept secret to avoid provoking a hostile retaliatory response.
- As a student, I want a way to report sensitive information without sharing who I am, so I can help to make change without impacting my educational experience.
- As a business leader, I want to make my team feel like they can share sensitive information without risking their career, so I can build trust in the team with which I work.
- As a source, I need a way to access someone's Hush Line, even if the Tor Network and the original URL are blocked in my country, so I can share information even in the most oppressive environments.

## 3. System Requirements
Hush Line is an open-source application tailored for Debian-based Linux systems [^14]. Debian is chosen for its stability and secure environment, beneficial for applications focusing on security.

### 3.1 Processor and Cryptography
The application requires a 64-bit processor, primarily to support contemporary cryptographic packages. These packages are integral to the security of Hush Line, as they enable the application to use advanced encryption methods necessary for protecting user data. The use of a 64-bit architecture allows the application to utilize these cryptographic techniques effectively.

### 3.2 Hardware Requirements
Hush Line is designed to be resource-efficient, with minimal hardware requirements, making it accessible on various devices.

- **Storage:** A minimum of 16 GB of storage is recommended. This specification is to accommodate the storage needs for encrypted messages, particularly for users who do not use email delivery. This storage capacity is intended to manage a significant amount of data and prevent issues related to storage space.
- **RAM:** At least 256 MB of RAM is suggested for optimal performance. This recommendation is based on ensuring smooth operation of the application, including updates, reboots, and other system processes [^15]. The moderate RAM requirement helps in maintaining the application’s performance across different systems, including older models with limited hardware capabilities.

### 3.3 Security and Privacy
The system requirements for Hush Line are set with a focus on maintaining its security and privacy features. By aligning with Debian-based Linux systems and modern cryptographic standards, the application aims to provide a secure platform for managing confidential communications.

## 4. Hush Line: The People's Tip Line
### 4.1. Goals
Hush Line aims to address key needs in the tip line ecosystem:

- **Access to non-technical users** - Users have multiple configuration options, including a consumer device called the Personal Server for a no-terminal setup or a one-line command to begin a fully-guided install process [^16].
- **Reduced attack surface** - Hush Line is a one-way, text-only messenger, removing the threat of receiving dirty data or malicious files.
- **Fewer requirements for usage** - Since Hush Line delivers messages to a user's email address, owners do not have to log in to a new platform to check their messages. 
    
By comparison, while fully featured, other tip lines require more complex setup processes and sometimes special infrastructure to operate correctly [^17]. A downstream effect of setups like this is that they require more people time to operate, leading to increased costs and higher risks to an organization's network.

### 4.2. Threat Model and Scope
Giving owners an option for the correct deployment for their specific use case and threat level is a crucial differentiator for Hush Line:

- High Threat - Considered for journalists, activists, or other human rights defenders. These individuals must consider threats to physical and digital safety. Protecting their server and user's location is critical.
- Medium Threat - Considered for business or government use cases. These individuals often are laypeople who are driven by moral conviction. Having the option for an onion or public tip line is essential.
- Low Threat - Considered for education settings and small businesses. Individuals need easy, uncomplicated access to the tip line. These users may not know about or could be intimated by an onion address.

In all cases, if an attacker were to gain access to the server, no sensitive information is stored there. Messages are encrypted before being saved or sent, instructions guide the user to use an app-specific password, ensuring full-account compromise is impossible, and public web deployments use HTTPS for data security in transit.

### 4.3. System Architecture
Hush Line's strong security comes from its simplicity. Since a sender is restricted to text-only messages, managing files, which requires new and sometimes prohibitively complex workflows, is avoided.

<img src="https://raw.githubusercontent.com/scidsg/project-info/main/hush-line/2.%20Design/arch.png">

### 4.4. Application

The application is written in Python and uses core libraries, including pgpy and smtplib [^18][^19]. There are three routes: 1. `/`, which displays the tip line owner's information extracted from their public PGP key, 2. `/info`, which provides end-users with helpful information about tip line usage, and 3. `/send_message,` which encrypts, then emails the message to the owner [^20].

```python
from flask import Flask, render_template, request, jsonify, redirect, url_for
import os
import pgpy
import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
import logging

# setup a logger
log = logging.getLogger(__name__)
log.setLevel(os.environ.get("LOG_LEVEL", "INFO").upper())
handler = logging.StreamHandler()
handler.setFormatter(logging.Formatter("%(asctime)s - %(levelname)s - %(message)s"))
log.addHandler(handler)
log.info("Starting Hush Line")

app = Flask(__name__)

sender_email = os.environ.get("EMAIL", None)
sender_password = os.environ.get("NOTIFY_PASSWORD", None)
smtp_server = os.environ.get("NOTIFY_SMTP_SERVER", None)
smtp_port = int(os.environ.get("NOTIFY_SMTP_PORT", 0))

if not sender_email or not sender_password or not smtp_server or not smtp_port:
    log.warn(
        "Missing email notification configuration(s). Email notifications will not be sent."
    )

# Load the public key into memory on startup
with open("public_key.asc", "r") as key_file:
    key_data = key_file.read()
    PUBLIC_KEY, _ = pgpy.PGPKey.from_blob(key_data)  # Extract the key from the tuple

def encrypt_message(message):
    encrypted_message = str(PUBLIC_KEY.encrypt(pgpy.PGPMessage.new(message)))
    return encrypted_message

@app.route("/")
def index():
    owner, key_id, expires = pgp_owner_info_direct()
    return render_template(
        "index.html",
        owner_info=owner,
        key_id=key_id,
        expires=expires,
        pgp_info_available=bool(owner),
    )

def pgp_owner_info_direct():
    owner = f"{PUBLIC_KEY.userids[0].name} <{PUBLIC_KEY.userids[0].email}>"
    key_id = f"Key ID: {str(PUBLIC_KEY.fingerprint)[-8:]}"
    if PUBLIC_KEY.expires_at is not None:
        expires = f"Exp: {PUBLIC_KEY.expires_at.strftime('%Y-%m-%d')}"
    else:
        expires = f"Exp: Never"
    return owner, key_id, expires

@app.route("/info")
def info():
    return render_template("info.html")

@app.route("/send_message", methods=["POST"])
def send_message():
    message = request.form["message"]
    encrypted_message = encrypt_message(message)
    with open("messages.txt", "a") as f:
        f.write(encrypted_message + "\n\n")
    send_email_notification(encrypted_message)
    
    return render_template("message-sent.html")

def send_email_notification(message):
    msg = MIMEMultipart()
    msg["From"] = sender_email
    msg["To"] = sender_email
    msg["Subject"] = "🤫 New Hush Line Message Received"

    body = f"{message}"h
    msg.attach(MIMEText(body, "plain"))

    try:
        with smtplib.SMTP_SSL(smtp_server, smtp_port) as server:
            server.login(sender_email, sender_password)
            server.sendmail(sender_email, sender_email, msg.as_string())
    except Exception as e:
        log.error(f"Error sending email notification: {e}")

if __name__ == "__main__":
    app.run()
```

### 4.4.1. Encryption
Hush Line uses open encryption protocols, including PGP (Pretty Good Privacy) and HTTPS (hypertext transfer protocol secure) [^21][^22].

#### 4.4.1.1. Client vs. Server-Side Encryption
We utilize server-side encryption so that users of Tor Browser's safest setting can use Hush Line without worry [^23]. Another factor determining client vs. server encryption is the question of server trust. Should the server see unencrypted content, even if it's never saved to disk? The main argument for client-side encryption is that if the server is compromised, the browser should handle the message encoding to avoid the need to trust the server. We observe two counterpoints: 1. If the server does become compromised, that would mean the client-side code could also be compromised, adding no significant security properties, and 2. we want the app to optimize for individuals needing the highest levels of protection within Tor Browser.

#### 4.4.1.2. Pretty Good Privacy
PGP, invented by Phil Zimmermann in 1991, is an open standard used across use cases for secure messaging [^24]. Many tools have been created to increase the usability of the protocol, making it easy for regular people to use. Hush Line's documentation recommends using Mailvelope, a browser extension that makes PGP work seamlessly with webmail clients [^25][^26].

### 4.4.2. Email Delivery
Hush Line delivers encrypted messages to an email address instead of requiring the tip line owner to log into an application to access communications.

#### 4.4.2.1. Simple Mail Transfer Protocol
SMTP, created by Jon Postel and Suzanne Sluizer in 1981, and despite many alternative technologies since, claims half the world's population at 4.26 billion users and 80% of all internet users [^27][^28][^29]. A goal for Hush Line is to limit the number of new applications someone needs to adopt in order to use our application, and indeed, all someone needs is Firefox or Chrome and an SMTP-compatible email provider like Gmail or Riseup.net [^30][^31][^32][^33].

### 4.4.3. Hush Line Service
Whenever the system operating Hush Line reboots, the application will automatically start, ensuring high reliability. During the installation process, a systemd service is created, which starts the application automatically [^34]:

```bash
# Create a systemd service
cat >/etc/systemd/system/hushline.service <<EOL
[Unit]
Description=Hush Line Web App
After=network.target
[Service]
User=root
WorkingDirectory=$HOME/hushline
EnvironmentFile=-/etc/hushline/environment
ExecStart=$PWD/venv/bin/gunicorn --bind 127.0.0.1:5000 app:app
Restart=always
[Install]
WantedBy=multi-user.target
EOL
```

### 4.4.4. Logging 
Hush Line does not log the IP address or location of end-users. We began with work from Guardian Project that uses custom formatting so IPs are saved as 0.0.0.0 [^35][^36]. We took it a step further and removed country-code logging, too [^37]. We include a custom nginx.conf file:

```
user www-data;
worker_processes auto;
pid /run/nginx.pid;
include /etc/nginx/modules-enabled/*.conf;
events {
        worker_connections 768;
        # multi_accept on;
}
http {
        ##
        # Basic Settings
        ##
        sendfile on;
        tcp_nopush on;
        types_hash_max_size 2048;
        # server_tokens off;
        server_names_hash_bucket_size 128;
        # server_name_in_redirect off;
        include /etc/nginx/mime.types;
        default_type application/octet-stream;
        ##
        # SSL Settings
        ##
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3; # Dropping SSLv3, ref: POODLE
        ssl_prefer_server_ciphers on;
        ##
        # Logging Settings
        ##
        # access_log /var/log/nginx/access.log;
        error_log /var/log/nginx/error.log;
        ##
        # Gzip Settings
        ##
        gzip on;
        # gzip_vary on;
        # gzip_proxied any;
        # gzip_comp_level 6;
        # gzip_buffers 16 8k;
        # gzip_http_version 1.1;
        # gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;
        ##
        # Virtual Host Configs
        ##
        include /etc/nginx/conf.d/*.conf;
        include /etc/nginx/sites-enabled/*;
        ##
        # Enable privacy preserving logging
        ##
        log_format privacy '0.0.0.0 - $remote_user [$time_local] "$request" $status $body_bytes_sent "$http_referer"';

        access_log /var/log/nginx/access.log privacy;
}
```

Below is a snippet of the logs from our demo application `try.hushline.app` after a user loads the URL and sends a message:

```
0.0.0.0 - - [21/Nov/2023:16:30:50 +0000] "GET / HTTP/1.1" 200 1135 "-"
0.0.0.0 - - [21/Nov/2023:16:30:50 +0000] "GET /static/style.css HTTP/1.1" 200 8074 "-"
0.0.0.0 - - [21/Nov/2023:16:30:50 +0000] "GET /static/fonts/mono/IBMPlexMono-Regular.woff HTTP/1.1" 200 57132 "-"
0.0.0.0 - - [21/Nov/2023:16:30:50 +0000] "GET /static/fonts/sans/AtkinsonHyperlegible-Regular.woff HTTP/1.1" 200 30380 "-"
0.0.0.0 - - [21/Nov/2023:16:30:50 +0000] "GET /static/fonts/serif/PlayfairDisplay-Medium.woff HTTP/1.1" 200 97576 "-"
0.0.0.0 - - [21/Nov/2023:16:30:50 +0000] "GET /static/favicon/favicon-16x16.png HTTP/1.1" 200 749 "-"
0.0.0.0 - - [21/Nov/2023:16:30:50 +0000] "GET /static/favicon/android-chrome-512x512.png HTTP/1.1" 200 36753 "-"
0.0.0.0 - - [21/Nov/2023:16:31:46 +0000] "POST /send_message HTTP/1.1" 200 540 "-"
0.0.0.0 - - [21/Nov/2023:16:31:46 +0000] "GET /static/style.css HTTP/1.1" 304 0 "-"
```

### 4.4.5. Censorship Resistance with Sauteed Onions
When deploying to a public website, Hush Line uses a new onion binding technique called sauteed onions to help increase its resistance to censorship [^38]. The method, created by Paul Syverson, Rasmus Dahlberg, Linus Nordberg, and Matthew Finkel, binds an onion address to a public domain name using TLS certificates. Using a domain's DNS settings, creating a CNAME record for `onion.acme.com` allows an HTTPS certificate to be issued, making the onion address discoverable in CT logs.

## 5. Personal Server
The Hush Line Personal Server is a physical Tor-only tip line device. Setup is completed outside the terminal, requiring no code, manually editing files, or logging in to a server [^39].

<img src="https://user-images.githubusercontent.com/28545431/281176815-9af0cfb8-8ca2-49ed-b7fc-d14b7c32ab5c.gif">

### 5.1. Threat Model
The Personal Server is designed for those needing complete infrastructure control. Since the device deploys to a Tor-only instance, it's recommended for journalists or human rights defenders who need the highest levels of anonymity for their server and users.

### 5.2. Hardware
Personal Server comes in a custom-designed, security-focused case made exclusively for Hush Line. A Raspberry Pi 4 powers the tip line, and a Waveshare 2.7" e-Paper display guides the owner through setup and usage [^40][^41]. 

### 5.3. Physical Security
We designed a custom, security-centric case that only exposes the device's power and ethernet ports; the USB, mini HDMI, audio, and SD card ports are inaccessible, helping to reduce the risks of tampering. A uniquely numbered tamper-evident sticker connected to the lid and case indicates if the device internals were physically accessed. When the device is issued to an owner, they're notified of the sticker seal's number, allowing for easy verification upon receipt.

### 5.4. Setup
While the core Hush Line app is identical to the software on the Personal Server, the physical device affords a more consumer-like setup process. Upon first boot, when an ethernet cable is connected, a QR code displays on the e-Paper screen, linking to a locally hosted web form to complete setup. The user will complete the installation by entering the information needed in a web form [^42]. 

```python
from flask import Flask, request, render_template, redirect, url_for
import json
import os
import smtplib
import segno
import requests
import socket
import gnupg

app = Flask(__name__)
gpg = gnupg.GPG()

# Flag to indicate whether setup is complete
setup_complete = os.path.exists('/tmp/setup_config.json')

def test_smtp_credentials(email, password, server, port):
    """Function to test SMTP credentials."""
    try:
        with smtplib.SMTP_SSL(server, int(port)) as smtp:
            smtp.login(email, password)
            return True
    except:
        return False

def validate_pgp_key(pgp_key):
    """Function to validate a PGP public key."""
    # Basic format check
    if not (pgp_key.startswith('-----BEGIN PGP PUBLIC KEY BLOCK-----') and
            pgp_key.endswith('-----END PGP PUBLIC KEY BLOCK-----')):
        return False

    # Import the key to check validity
    import_result = gpg.import_keys(pgp_key)

    # Check if the key was imported successfully
    if not import_result.count:
        return False

    return True  # If all checks pass, the key is valid

@app.route('/setup', methods=['GET', 'POST'])
def setup():
    global setup_complete
    if setup_complete:
        return redirect(url_for('index'))

    error_msg = None
    if request.method == 'POST':
        email = request.form.get('email')
        smtp_server = request.form.get('smtp_server')
        password = request.form.get('password')
        smtp_port = request.form.get('smtp_port')
        pgp_public_key = request.form.get('pgp_public_key')

        if not test_smtp_credentials(email, password, smtp_server, smtp_port):
            error_msg = "⛔️ SMTP credentials are invalid. Please check your SMTP server address, port, email, and password, and try again."
        elif not validate_pgp_key(pgp_public_key):
            error_msg = "⛔️ PGP key is invalid. Please check your PGP key and try again."
        else:
            # Save the configuration
            with open('/tmp/setup_config.json', 'w') as f:
                json.dump({
                    'email': email,
                    'smtp_server': smtp_server,
                    'password': password,
                    'smtp_port': smtp_port,
                    'pgp_public_key': pgp_public_key
                }, f)

            setup_complete = True

            # Save the provided PGP key to a file
            with open('/home/hush/hushline/public_key.asc', 'w') as keyfile:
                keyfile.write(pgp_public_key)

            return redirect(url_for('index'))

    return render_template('setup.html', error=error_msg)

@app.route("/")
def index():
    if not setup_complete:
        return redirect(url_for("setup"))
    return render_template("success.html")

if __name__ == '__main__':
    qr = segno.make(f'https://hushline.local/setup')
    with open("/tmp/qr_code.txt", "w") as f:
        qr.terminal(out=f)
    app.run(host='0.0.0.0', port=5001)
```

## 6. Research
Hush Line relies on our users to help inform us about their needs and ways in which we might be able to better support them. To this end, we've created interview guides, launched asynchronous surveys, and speak directly to the available individuals and organizations using Hush Line [^43][^44]:

### 6.1. Interview Guides
- **Purpose:** The interview guides are designed to obtain in-depth, qualitative data from users about their experiences with Hush Line. This approach is particularly useful for understanding nuanced user behavior and preferences that might not be apparent in quantitative data.
- **Methodology:** These interviews could be conducted using various formats, such as face-to-face, telephonic, or video calls. They might include open-ended questions to encourage users to share their stories and experiences in a conversational manner.
- **Impact:** The insights gained from these interviews can lead to a deeper understanding of user needs, allowing Hush Line to tailor its services more effectively. For instance, uncovering specific pain points could lead to targeted improvements in the app's interface or functionality.

### 6.2. Asynchronous Surveys
- **Purpose:** Asynchronous surveys offer a scalable way to collect feedback from a broad user base, allowing for a more generalized understanding of user satisfaction and areas of improvement.
- **Methodology:** These surveys might include a mix of multiple-choice questions, Likert scale questions (for measuring attitudes), and open-ended questions. They can be distributed through email campaigns, embedded within the Hush Line app, or shared on social media platforms.
- **Impact:** The data collected can help in identifying trends, common issues, and areas where users are most satisfied. This can guide strategic decisions and prioritization in the development roadmap of Hush Line.

### 6.3. Direct Communication with Users and Organizations
- **Purpose:** Engaging directly with users and organizations helps in building a community around Hush Line and provides a platform for detailed and personalized feedback.
- **Methodology:** This might involve scheduled calls, feedback sessions, or interactive Q&A sessions with users. It could also include regular check-ins with organizations that use Hush Line for their operations.
- **Impact:** Such interactions not only provide valuable insights but also foster a sense of community and loyalty among users. They can reveal specific use cases and success stories that can be used for marketing and further development of Hush Line.

## 7. Auditing Hush Line
Before recommending Hush Line be adopted for use cases from journalism, education, and business, we wanted to have independent audits of key areas of the application. All of the work below was sponsored by Open Tech Fund through their Secure Usability and Accessibility and Red Team labs [^45][^46][^47].

### 7.1. Accessibility
In Q3-2023, A11y Lab conducted an accessibility audit of Hush Line's website and web application according to the international standard Web Content Accessibility Guidelines 2.1 (WCAG 2.1), which is divided into four principles (Perceivable, Operable, Understandable, and Robust), thirteen guidelines that contain requirements (success criteria) and three levels of conformance A, AA and AAA [^48][^49]. The findings included:

- target size,
- bypass blocks,
- textarea focus,
- contrast levels,
- sensory characteristics,
- info and relationships,
- link purpose,
- labels or instructions,
- focus visibility, and
- page titles.

Soon after receiving the report, all findings were addressed [^50].

### 7.2. Security [IN-PROGRESS]
In Q4-2023, Subgraph conducted a security audit of Hush Line's core app and the Personal Server device [^51].

## 8. External Collaboration
Similar to the audits above, we worked with OTF's SUA Lab and engaged with Plaintext and Ura Creative to improve our homepage's visual design and content at hushline.app. 

### 8.1. Content Design
In Q2-2023, we worked with Plaintext Design to help us think through how we communicate using our homepage [^52][^53]. The key takeaways were to bring greater density to the interface and more concrete language in the heading of our intro section. 

### 8.2. Visual Design [IN-PROGRESS]
In Q4-2023, we worked with Ura Creative to assist in developing Hush Line's visual identity, including illustrations, iconography, identity, and marketing assets [^54]. 

## 9. Documentation
Hush Line aims to write simple, straightforward documentation for non-technical users [^55]. 

## 10. Support Model
While Hush Line is free and open-source software, we recognize the need for financial support for our contributors and professional support for the product. We've set up multiple ways for support, including:
- GitHub Sponsors
- Open Collective
- Community Contributor Guidelines

We aim for a scalable, repeatable framework for which all products can follow [^2][^56][^57].

## 11. Challenges
### 11.1. Financial Support
The most significant challenge Hush Line has experienced is funding. The product is entirely self-funded and volunteer-driven, and finding sustainable support will be a long-term goal for the team.

## 12. Future Work
### 12.1. Personal Server
In Q1 of 2024, the Personal Server will launch with a limited production run. The goal of the launch is to raise capital for future product development. 

### 12.2 Hosted Service
Hush Line is currently completely decentralized. Science & Design operates no infrastructure supporting the operation of current instances, so there isn't a single way to block them all. While the security properties of our initial approach will always be an option moving forward, we're considering other ways to make Hush Line available to more people who may need it. One approach could be a centralized service, similar to any SaaS product like Proton, Facebook, or Google, where a user clicks "New Account" or something similar to sign up and use the app [^58][^59][^60].

#### 12.2.1 Risks
The risks from centralizing any service includes becoming a target whose attack could disrupt a large set of individual users. Whether an SMTP or account-based service, we would need to carefully plan the most resilient architecture to protect our customers.

## 13. Hush Line Contributors
- Glenn Sorrentino, Design, Engineering [^61]
- Sam Schlinkert, Documentation, Engineering [^62]
- Saptak Sengupta, Accessibility, Engineering [^63]
- Abbey Ripstra, Research [^64]
- Dr. Ashley Di Battista, Research [^65]
- Micah Lee, Engineering [^66]
- Grant Birkinbine, Engineering [^67]
- Simon Wörpel, Engineering [^68] 
- Em, Privacy Engineering [^69] 
- Dr. Florian Idelberger, Engineering [^70]
- Chirayu Desai, Privacy Engineering [^71]
- Scott Jenson, Content Design [^72]
- Ura Creative, Visual Design [^52]
- Stef Daehler, Subject Matter Expert, Education [^73]
- Dr. Martin Shelton, Subject Matter Expert, Journalism [^74]
- Ese Udom, Android Engineering [^75]
- Alex Rojas, Industrial Design [^76]

## References
[^1]: https://hushline.app 
[^2]: https://github.com/scidsg/hushline
[^3]: https://github.com/scidsg/hushline/blob/main/LICENSE
[^4]: https://securedrop.org
[^5]: https://globalleaks.org
[^6]: https://signal.org
[^7]: https://itif.org/publications/2021/11/29/assessing-state-digital-skills-us-economy/
[^8]: https://letsencrypt.org/
[^9]: https://tb-manual.torproject.org/onion-services/
[^10]: https://www.nytimes.com/2004/02/06/opinion/the-journalist-and-the-whistle-blower.html
[^11]: https://www.theguardian.com/world/2013/aug/18/glenn-greenwald-guardian-partner-detained-heathrow
[^12]: https://hbr.org/2020/10/do-your-employees-feel-safe-reporting-abuse-and-discrimination
[^13]: https://theconversation.com/culture-of-trust-is-key-for-school-safety-92731
[^14]: https://www.debian.org/
[^15]: https://www.privex.io/articles/setup-tor-hidden-service-website/
[^16]: https://github.com/scidsg/hushline/tree/personal-server
[^17]: https://docs.securedrop.org/en/stable/admin/installation/hardware.html
[^18]: https://pypi.org/project/PGPy/
[^19]: https://docs.python.org/3/library/smtplib.html
[^20]: https://github.com/scidsg/hushline/blob/main/app.py
[^21]: https://www.openpgp.org/
[^22]: https://en.wikipedia.org/wiki/HTTPS
[^23]: https://tb-manual.torproject.org/security-settings/
[^24]: https://en.wikipedia.org/wiki/Pretty_Good_Privacy
[^25]: https://scidsg.github.io/hushline-docs/book/prereqs/general.html#3-mailvelope
[^26]: https://mailvelope.com/en
[^27]: https://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol
[^28]: https://www.statista.com/topics/4295/e-mail-usage-in-the-united-states/#editorsPicks
[^29]: https://www.statista.com/statistics/617136/digital-population-worldwide/
[^30]: https://www.mozilla.org/en-US/firefox/new/
[^31]: https://www.google.com/chrome/
[^32]: https://mail.google.com/mail/
[^33]: https://riseup.net/
[^34]: https://github.com/scidsg/hushline/blob/main/assets/scripts/install-tor-only.sh
[^35]: https://f-droid.org/en/2019/04/15/privacy-preserving-analytics.html
[^36]: https://guardianproject.info/
[^37]: https://github.com/scidsg/hushline/blob/personal-server/assets/nginx/nginx.conf
[^38]: https://www.sauteed-onions.org/
[^39]: https://github.com/scidsg/hushline/tree/personal-server
[^40]: https://www.raspberrypi.com/products/raspberry-pi-4-model-b/
[^41]: https://www.waveshare.com/2.7inch-e-paper-hat.htm
[^42]: https://github.com/scidsg/hushline/blob/personal-server/assets/python/web_setup.py
[^43]: https://cryptpad.fr/form/#/2/form/view/aznAzzpG6Fh3K1Dq0JjslCK-NmSugmfLTP7ej+SqRl0/
[^44]: https://cryptpad.fr/form/#/2/form/view/UkUurwNmHbV1wM8n82djr9F8G3N0gEAXytMVxTWirfY/
[^45]: https://www.opentech.fund/
[^46]: https://www.opentech.fund/labs/red-team-lab/
[^47]: https://www.opentech.fund/labs/sua-lab/
[^48]: https://www.a11ylab.com/
[^49]: https://github.com/scidsg/project-info/blob/main/hush-line/1.%20Accessibility/WCAG%202.1%20AAA_HushLine%20website.pdf
[^50]: https://github.com/scidsg/hushline/issues?q=is%3Aissue+is%3Aclosed+A11y+Lab+
[^51]: https://subgraph.com/
[^52]: https://plaintext.design/
[^53]: https://docs.google.com/presentation/d/1ugXg9xYopR_EhjDRbv14jp_Bef-vrmQgztD5aO5sDyg/edit?usp=sharing
[^54]: https://ura.design/en/
[^55]: https://scidsg.github.io/hushline-docs/book/intro.html
[^56]: https://opencollective.com/scidsg
[^57]: https://github.com/scidsg/hushline#contribution-guidelines
[^58]: https://proton.me/
[^59]: https://www.facebook.com/
[^60]: https://www.google.com/
[^61]: https://glennsorrentino.com/
[^62]: https://github.com/sts10
[^63]: https://saptaks.website/
[^64]: https://www.linkedin.com/in/abigailripstra/
[^65]: https://www.linkedin.com/in/ashley-di-battista-phd-1891a1253/
[^66]: https://micahflee.com/
[^67]: https://github.com/GrantBirki
[^68]: https://simonwoerpel.github.io/
[^69]: https://infosec.exchange/@Em0nM4stodon/
[^70]: https://www.linkedin.com/in/florianidelberger/
[^71]: https://www.linkedin.com/in/chirayu-desai-044788131/
[^72]: https://www.linkedin.com/in/scottjenson/
[^73]: https://www.linkedin.com/in/stefaniedaehler/
[^74]: https://freedom.press/people/martin-shelton/
[^75]: https://www.linkedin.com/in/eseudom/
[^76]: https://www.linkedin.com/in/axel-rojas/
