# Code-server Engineered by OCTOPODAMI (CSEO) Setup

Our pre-configured stack relies on AWS EC2 which helps to improve performance and scalability of your code-server instance, but additional integration with other AWS services like S3, CloudFront, Route53, and Auto Scaling is possible.

## Preliminary Setup

You need to create a unique EC2 Key Pair so you can log into your EC2 instance easily. Within the AWS Management Console:

1. Go to **EC2** > **Network & Security** > **Key Pairs**
2. Click **Create Key Pair**
3. Enter a Key pair name and click **Create**
4. Download your Key pair with a **.pem** extension and store it in a safe place on your computer.

## Launch Instance

Within the EC2 Dashboard page, you can do the following to launch a Code-server Engineered by OCTOPODAMI (CSEO) instance:

1. Click the **Launch Instance** button or click this button [![Launch Stack](./images/launch-stack.png?raw=true)](https://aws.amazon.com/marketplace/pp/prodview-hwp3orchrmnpk)
2. Next, click **AWS Marketplace** tab on the left side of the **Choose an Amazon Machine Image (AMI)** page
3. Enter the phrase **octopodami** in the search box and press **enter** on your keyboard
4. Click the **select** button in front of Code-server Engineered by OCTOPODAMI®
5. Click the **continue** button in the dialog box
6. Select an instance type that fits your budget then click the **Review and Launch** button
7. Configure these options (**Security Groups**, **Instance Details**, **Storage**, and **Tags**) to match your business needs
8. Click the **launch** button

## Setup Your Code-server Instance

Within the EC2 Dashboard page, click **Instance** to view your running instance, if any.

1. Select the instance you launched to view its detailed descriptions
2. Click the icon in front of **IPv4 Public IP** to copy the IP Address of the server to clipboard
3. Paste the IP Address in your browser (Chrome, Firefox, and IE. e.t.c.) on port 8080 (e.g., http://your-ip:8080)
4. You will be presented with the initial code-server setup screen

5. Copy the **Instance ID** from your EC2 dashboard, paste it in the input field and click the **Unlock Octopodami** button to proceed
6. That's all you have to do. You will now be able to access your new code-server instance at http://your-instance-ip:8080
7. Your login credential is available here in the EC2 Instance: `sudo cat /root/.code-server-credentials`

**Please Note**: the IP Address above is not a real one -- yours will be unique. :wink:

Use the credentials you provided during setup to access the code-server admin console. You can now create projects, install extensions, and configure your VS Code development environment.

![Rejoice](https://media.giphy.com/media/26xBFFYvGNMfPo9QQ/giphy.gif?raw=true "Rejoice")

## Wanna Geek Out? SSH Into The Server

To SSH into your EC2 instance:

1. ```cd``` to the location of your .pem key
2. Run ```chmod 600 mykey.pem``` to lock down your SSH key
3. Run ```ssh -i /path/my-key-pair.pem ec2-user@<your ip address>```
4. Bam!!! Have fun. Don't break anything, but if you do. Support is available [here](mailto:tech@cloudeya.org).

## Links

1. [Product Website](https://aws.amazon.com/marketplace/pp/prodview-iyn7nuvxxqcjg)
2. [EULA](./octopodamiEULA.txt)
3. [Knowledgebase](https://github.com/cloudeyalimited/code-server-engineered-by-octopodami/-/wikis/home)
4. [Issue Tracking](https://github.com/cloudeyalimited/code-server-engineered-by-octopodami/-/issues)
5. [Changelog](./changelog.md)

## Support

[Email](mailto:tech@cloudeya.org) support is available to Amazon Web Services Marketplace Customers. We do not offer refunds, but you may terminate your Code-server Engineered by OCTOPODAMI (CSEO) Stack at any time.

## License

The documentation is published under [BSD 3-Clause License](license.txt).

## Copyright

(c) 2020 - 2025 [Cloudeya Limited](https://cloudeya.org).