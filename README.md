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

let's head back into the S3 bucket and change the permissions. Click on the permissions tab then on Edit within the Block public access (bucket settings) section.

![Snipe 6](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/3c85e9b5-4360-4801-9ba7-bc773252d113)

Uncheck Block all public access then save the changes.

![Snipe 7](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/c4be4dfd-7625-4835-95f6-8a49da4b1fb6)

You will now need to type in confirm in the field in order to continue with the permission change.

*This next step I actually forgot to do at first* The second step in this process is to go back into the S3 bucket permissions scroll down to Object Ownership and click on the Edit button. Click on ACLs enabled, acknowledge that ACL’s will be restored then save the changes.

![Snipe 8](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/e6b32f5a-7247-44cf-9c47-00b471ea4be2)

Now scroll down to Access control list (ACL) and click on Edit. We are going to give the Everyone group Read access on the Bucket ACL. You will have to check “I understand the effects of these changes on my objects and buckets” before you can proceed then click Save changes.

![Snipe 9](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/3b39442e-c007-4f5f-ab40-b0a35683d5c9)

The final step is to click on the checkbox next to the index.html file, click on the Actions button, then click on Make public using ACL. Then click on Make Public.

![Snipe 10](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/d99be480-da7c-4c23-91f7-0365dd5deb5b)

Step 3: Verifying that we can access the website via the internet. Now we need to check to see if we can access the website using the bucket website endpoint URL and not the object URL. Go back into your bucket and click on the properties tab. Scroll down to Static website hosting and copy the bucket website endpoint URL. Open a browser in incognito mode and paste the link into the address bar and hit enter.

![Snipe 11](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/c575ba35-3ee1-444d-bf77-16d9f84b16f0)

As you can see, the website is now working within the S3 bucket. With that, Tier 1 has been completed. let’s go on to Tier 2 Advanced.

# Tier 3: Advanced

The goals for this tier are:
— Use CloudFront along with our S3 Static hosted website to take advantage of Edge Caching for better performance
— Ensure the CloudFront URL can only be accessed through HTTPS and that any HTTP traffic is redirected to HTTPS
— Verify you can reach the website using the CloudFront URL and make sure the URL redirects HTTP to HTTPS
— Verify that caching is working by making a small change to the HTML code

Let’s get started working on Tier 2.

First thing we need to do is navigate over to CloudFront. Click on Create a CloudFront distribution.

Now in Origin domain, click in the dropdown box and select your website S3 bucket. You will be presented with the following message:

![Snipe 12](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/26ee8e23-298b-4b75-809c-43ae90641b06)

Do not click on Use website endpoint

Scroll down to Origin access. This next step is actually meeting part of Tier 3’s requirement but we are here at the moment so might as well take care of this now. Change the Origin Access to Origin access control settings (recommended). Changing this allows the bucket to only provide the access to CloudFront. The other requirement of Tier 3 will wait until we get there. Once the CloudFront distribution is created, it will provide us with a bucket policy that we must add manually in S3.

![Snipe 13](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/e6f5d949-8ace-49e7-a779-68281f7baa94)

In Origin access control, click on the button Create control setting. You can leave everything as default and click on Create.

![Snipe 14](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/c276c1c0-52a5-4f9b-82aa-1dad2a8608bb)

Ignore the Origin access control is required message for now. This gets taken care of once you apply the bucket policy in S3.

Please scroll down to Default Cache behavior. Since there are requirements to ensure that the CloudFront URL can only be accessed through HTTPS as well as making sure that HTTP gets redirected to HTTPS, we will change the option to Redirect HTTP to HTTPS.

Scroll down to WAF and select Do not enable security protection. (Only because this is a sandbox. In the real world we would need to add this protection. Especially for a banking website)

Since we will not be purchasing a domain, we can skip the SSL certificate section and keep scrolling to the bottom. Now click on Create distribution.

You should see up top in a blue banner: The S3 bucket policy needs to be updated. Click on the Copy policy button to the right.

![Snipe 15](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/05547ded-c04a-4595-b0c1-92998c84589d)

Open the S3 console in another tab and head over to permissions for your website bucket. In the Bucket policy section, click on Edit. Then paste the policy and click on Save changes.

![Snipe 16](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/9acc4ed2-3bc8-46c7-8838-98ef119e1daf)

Now we head back to our CloudFront distribution. Make sure the status is displaying Enabled before you continue.

![Snipe 17](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/add7deac-33c1-4270-88d7-76bd0cf2480f)

Click on the distribution, grab the distribution domain name and paste it into an incognito tab. Anddddd we got an access denied message…..sigh!!!

Let’s back up and see what we missed. From prior experience, I think I know what I left out. Let’s go back into the distribution settings section and click on Edit.

![Snipe 18](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/19fafccd-8cf0-4d4d-aa74-96a77c51b4f5)

Scroll down to Default root object and type in index.html then save the changes.

![Snipe 19](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/532e08ce-609f-4e62-8256-24c0788a3283)

The distribution will now start deploying the new change. This should take a few minutes to complete. After it is completed, grab the Distribution domain name again and paste it into the incognito tab.

The website is now working via CloudFront and it is using HTTPS!!!

![Snipe 20](https://github.com/Mirahkeyz/Hosting-a-static-website-on-AWS-S3-using-CloudFront/assets/134533695/1bcbf8f9-86ac-49bd-bd5e-dd2fc68c9f06)

Now, to see if we are able to meet the redirection requirement. Click in the address bar and change the HTTPS to HTTP then hit enter. Success!!!! HTTP is being redirected to HTTPS.
































































































