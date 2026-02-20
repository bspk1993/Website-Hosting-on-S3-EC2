# Website-Hosting-on-S3 & EC2


1.Firstly create the S3 bucket with required name as per Owner requirements

2. Take the code with HTML (file format)

3. Make changes in Properties --> Go to "static website Hosting " --> enable it --> Hosting type (Host a static website) --> Index document as index.html

4. Go to "Permission tab"  --> Block "Public Access' as OFF make the bucket policy as "EDIT"

   {
    "version": "2012-10-17",
    "statement": [
      {
        "sid": "PublicReadForStaticWebsite",
        "Effect": "Allow",
        "Principal": "*",
        "Action": "S3:GetObject",
        "Resource": "arn:aws:s3:::games/*"
        }
   ]
}

5. Do not make any changes in ACL (Access Control List)

Website hosting on EC2

1. Launch Ec2 ubuntu,after the running , connect to it

apt update
sudo apt install apache2 -y
sudo systemctl start apache2
sudo systemctl enable apache2
cd /var/www/html/index.html
mv index.html index.html.backup
sudo systemctl restart httpd
sudo systemctl restart apache2

2 Browse the public IP ---> Application will Run

---> when we want to our website which is in S3 bucket it will static website hosting only. so we get it in the https://.........com/ to make this the open in laptop but it will not open in the phones .To make this possible we need by https://.........net/
---> So we need to go the Cloudfront distribution
---> Create distribution in cloud front (CDN) --> Select Distribution type as "Single website or app" ---> select the "Amazon S3"
---> Give S3 bucket -->settings as code settings ---> Redirect HTTP to HTTPS ---> Allowed HTTP methods as GET,HEAD ---> Next ---> Create Distribution
