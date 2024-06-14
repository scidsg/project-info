# Threat Modeling for Hush Line Deployment

## Introduction
The deployment of an anonymous tip line, like Hush Line, requires an understanding of the environment in which it will be used. Different organizations and individuals face unique threats, and the purpose of this guide is to help you navigate these challenges. By understanding your threat landscape, you can choose the appropriate deployment method that balances accessibility and security for your needs.

## Understanding the Threats
To select the right Hush Line deployment, consider the potential risks and consequences you or your tipsters might face:

### Low Threats
These scenarios typically involve situations where the primary risk is non-targeted threats or generic cyber threats. The fallout from a security breach is minimal. 

We recommend using a VPS and deploying Hush Line as a public domain to a URL like this: `tips.acme.com`.

#### Examples
- 💼 Small to medium businesses
- 🏫 Schoolhouses
- 🎈 Conference organizers

### Medium Threats
Here, the risks escalate. They include targeted threats but might not require advanced defense measures. 

We recommend using a VPS and deploying Hush Line as a public domain to a URL like this: `tips.acme.com`. When sharing your Hush Line address, include the onion address for people that require higher levels of anonymity.

#### Examples
- 📈 Publicly traded businesses
- 🩺 Law or doctor's offices
- 🚨 Domestic abuse hotlines

### High Threats
These are scenarios where targeted threats are likely, and consequences can be severe, like endangering someone's physical safety.

Depending on risks to your physical location, we recommend either using a VPS or local device like a Raspberry Pi and choosing an onion-only deployment. This will provide the greatest protection for your community and your tip line.

#### Examples
- 📰 Journalists
- 🆘 Government whistleblowers
- 🚔 Locations with internet censorship

## Malicious Actors & Misinformation
Always be aware that anonymity can be a double-edged sword. While it provides protection for genuine whistleblowers, it can also shield malicious actors. Regularly vet and verify the tips you receive to guard against misinformation campaigns, especially in high-risk scenarios.

## Deployment Options
Given Hush Line's range of deployment choices, weigh the pros and cons of each:

- **Onion-only**: Best for high-threat environments, offering maximum anonymity. However, it might be less accessible for non-technical users.
  
- **Tor + Public Web**: Offers a balance of accessibility and security. Useful for medium-threat scenarios.

- **Physical Device**: This option, like deploying on a Raspberry Pi, gives you more control but could be at risk if the physical location is compromised. Ideal for high-risk scenarios where control over the infrastructure is crucial.

It's important for all deployment types to share your addresses with your community openly and clearly, and reinforce to your users to _only_ use the addresses that you've shared.

## Boosting Security
To further bolster security:

1. Use dedicated devices to check emails from Hush Line.
2. Employ secondary verification methods for significant tips.
3. Enhance anonymity with tools like VPNs or secure browsing techniques.

## Maintenance & Updates
While Hush Line offers automatic updates, it's vital to:

- Regularly review the system for potential threats.
- Stay informed about the latest security updates and patches.
- Engage in regular security training and awareness for all staff involved.

## Conclusion
Deploying Hush Line is a step towards fostering open communication while safeguarding anonymity. By understanding the threats, choosing the right deployment option, and following security best practices, you can ensure a secure and effective platform for your community.

*For organizations seeking in-depth threat analysis and tailored advice, please send an email to hushline@scidsg.org.*
