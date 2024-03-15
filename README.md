# Hosting-a-static-website-on-AWS-S3-using-CloudFront

Scenario Part 1: Level Up Bank is an imaginary fintech startup that provides banking services to its clients. The main channel for acquiring new customers and facilitating interaction with the bank is the company’s website. Presently, the website is hosted on a server located on-premises, necessitating an IT team exclusively dedicated to its management and upkeep. This arrangement incurs supplementary expenses for the company and introduces an extra layer of intricacy to the infrastructure.

To address these challenges, Level up Bank has decided to move its website to AWS S3. The change would provide the following benefits:

Cost Savings, Improved Scalability, High Availability and reduced management overhead.

Scenario Part 2:
Level Up Bank is experiencing a growing customer base accessing their website from various locations worldwide. Consequently, the website’s performance is deteriorating due to latency problems. Furthermore, the bank is concerned about safeguarding the website against cyber attacks. Additionally, Level Up Bank aims to reduce hosting expenses while simultaneously enhancing website performance and security.

To overcome these challenges, I recommend that Level Up Bank integrate AWS CloudFront into their S3 Hosted Static website. AWS CloudFront is a content delivery network (CDN) service that efficiently distributes static and dynamic web content, including HTML, CSS, JavaScript, images, and videos, to global users, ensuring minimal latency and rapid data transfer speeds. The benefits of this strategy are as follows:

Improved website performance, enhanced website security and reduced website hosting costs.

Project Overview: This project has 3 tiers of difficulty. Foundational, Advanced and Complex. I will be challenging myself to complete all 3 tiers and will be breaking down each tier’s goals and steps.

Prerequisites:

We are going to need an AWS account and an IDE to make small changes to the HTML file. I will be using VS Code.

# Tier 1: Foundational

The goals for this tier are:
— Create an S3 bucket using the AWS console and upload the index.html file.
— Modify the S3 bucket so that it can host a static website and can be reachable through the internet
— Verify internet access using the bucket website endpoint and not the object URL

Now that we are aware of what needs to be accomplished, lets get started!!!

Create the S3 Bucket and upload the index.html file. let’s log into our AWS account then head over to S3. Go ahead and click Create bucket. Now we need to name the bucket. I will be naming mine levelupbankwebsite. I am going to leave everything else as default for now. Scroll down and click on Create bucket.

![Snipe 1](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/be3adc7e-dd75-4fde-97f4-86582e990d8f)

![Snipe 2](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/106dd5ab-fed4-43bb-a1bf-09ef170e0fee)

Now that our bucket has been created, let’s upload the index.html file to the S3 bucket.

![Snipe 3](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/bb63238d-80d6-4765-a604-0c6c1f8305ef)

Static website. Now let’s modify our S3 bucket so that it can host a static website. Locate your bucket in S3 and click on it. Click on the Properties tab up top and scroll down to Static Website and click the Edit button on the right hand side.

![Snipe 4](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/6699b06f-9ba7-4a4f-a073-19c3725c3d45)

In the static website hosting page, Enable Static website hosting, leave Host a static website selected and for Index document, type in index.html then click on Save changes on the bottom of the screen.

![Snipe 5](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/4722f9f5-4a1d-4446-8ac7-df483c360865)

Now if you try to access the object URL, you will be presented with an access denied message. This is because currently the S3 bucket is set to not allow public access. lets go change that.




















