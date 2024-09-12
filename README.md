# 1. Host a Website on Amazon S3

**What is Amazon S3?**
Amazon Simple Storage Service(Amazon S3) is a scalable, high-performance object storage designed for large amounts of data. S3 allows you to store any type of file(images, videos,
documents, etc.) in what we call "buckets" making it ideal for use cases like data backup, content distribution, and even hosting static websites.

**How I Used Amazon S3 in This Project?**
For this project, I utilized Amazon S3 to host a static website, which is a website consisting of HTML, CSS, Image Assets and JavaScript files(no server-side processing).

**What I Didn’t Expect?**
One thing I didn't anticipate was the strict enforcement of AWS permissions. AWS takes security very seriously. Every action and access request is governed by permissions policies, ensurong that data is protected from unauthorized access.

**How long did it take?**
The overall setup took about **an hour**, largely because I followed a detailed guides by Natasha on Youtube using the link: ***https://www.youtube.com/watch?v=VfPj4JY-0P8&t=4s***, Her tutorials helped streamline the process and ensured I didn’t miss any key steps. I also took notes along the way, which helped with documenting the project.

# 2. Steps:

## 2.1 How I Set Up an S3 Bucket:

    Setting up an S3 bucket was quite straightforward and only took about 5 minutes, mostly because I was taking notes along the way. I chose the Europe (**Paris**) region (**eu-west-3**) for my bucket since it is the closest AWS region to Morocco, my location. This ensures lower latency for website visitors in the region.

    ![alt text](../screenshots/bucket-creation.PNG)

    **Key Points:**

    - Unique Bucket Name: S3 bucket names must be globally unique. This means there can only be one bucket with a given name across all AWS accounts, so I chose a specific and descriptive name for my project.

## 2.2 Upload Website Files to S3:

    After setting up the bucket, I uploaded my website files. These consisted of:
      - **index.html:** The main HTML file of the static website.
      - **Assets:** A folder containing the images, CSS and JavaScript files required for the website.
    Both the HTML file and the images are essential for the project. The index.html depends on the images for proper display, so it's important that they are in the correct folder structure.

    ![alt text](../screenshots/objects-upload.PNG)

## 2.3 Static Website Hosting on S3:

     Once the files were uploaded, the next step was to enable Static Website Hosting. This feature allows you to serve the website publicly over the internet.

     ~~Steps to Enable Static Website Hosting:~~
      - Go to the **Properties** tab of your S3 bucket.
      - Scroll down to the **Static Website Hosting** section
      - Check the option to enable static website hosting.

     Enabling this allows the bucket to serve your website files to visitors as if it were a web server.

## 2.4 Access Control Lists (ACLs):

    In order to make the website publicly accessible, I had to configure Access Control Lists (ACLs). ACLs are a set of permissions that dictate who can access certain resources within S3. For this project, I configured the bucket to be publicly accessible, allowing visitors to view the website.

## 2.5 Bucket Endpoints:

After enabling static website hosting, AWS generated a bucket endpoint URL. This is the public URL through which users can access the website.
Here’s the bucket endpoint URL for my project: **http://nextwork-website-project-nassimabr.s3-website.eu-west-3.amazonaws.com/**

![alt text](../screens/bucket-endpoints.PNG)

## 2.6 Troubleshooting an Error:

When I first visited the bucket endpoint, I encountered a **403 Forbidden** error. This error occurred because, while the bucket itself was public (due to the ACL settings), the **objects inside the bucket** (HTML and image files) were not yet publicly accessible.

![alt text](../screenshots/403-status.PNG)

**Fix:**
I adjusted the permissions for the individual files to make them public, which resolved the issue.

## 2.7 Success!:

    After adjusting the permissions for the files inside the bucket, I successfully accessed the website through the bucket endpoint without any issues.

## Final thoughts:

Hosting a static website on Amazon S3 is a cost-effective and straightforward process. The most challenging aspect of this project was ensuring the correct permissions, but once I understood how ACLs work, it was easy to configure.

This documentation should give a clear picture of how I set up my S3 bucket, uploaded files, enabled static website hosting, and dealt with potential errors.

Special thanks to **https://learn.nextwork.org/** for their guidance throughout this project. Their resources and tutorials were instrumental in helping me understand the process and successfully implement this solution.
