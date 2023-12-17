Expose Spring boot  API with nginx 
Introduction
    This tutorial will lead you to setup Amazon Linux 2023 EC2,nginx, for expose the Spring boot api with SSL enabled domain.
    We will discuss step by step
1. Launch EC2 instance - I am not going to explain this you can find many tutorials on this.
2. Install Java in Amazon Linux
    *   sudo yum update -y
    *   sudo yum install java-17
3. Create Elastic IP and associate it with the EC2 instance
4. Attach the domain in hosted zones of Route 53
    * create A record for Elastic IP address
    * create A record with WWW for Elastic IP Address
5. Modify security group which attached to the the EC2
    * Add inbound rule for spring boot application. create a custome port of your Spring application (Ex - 8080)
    * Add HTTPS for enable the SSL url
6. Install NGINX
    *   sudo yum install nginx
    *   sudo yum systemctl start nginx - to start the nginx srver
    *   curl localhost - Test the nginx is working or not,
7. Install certbot for implement SSL certificates for NGINX
    *   sudo yum install certbox-nginx
8. Modify NGINX configurations for attach the domain
    *   sudo vi /etc/nginx/nginx.conf
    *   Find the existing server_name line: server_name _;
    *   Replace the _ underscore with your domain name: server_name example.com www.example.com;
    *   Setting Up a Proxy Server
    *   modify the server 
    location /application1 {
        proxy_pass http://YOUR_ELASTIC_IP:8080/REST_OF_YOUR_URL;
    }
    *   save the file and quit your editor. If you are using vi, enter :x, then y when prompted, to save and quit. Verify the syntax of your configuration edits with: sudo nginx -t
    *   If that runs with no errors, reload Nginx to load the new configuration: sudo systemctl reload nginx
9. Obtaining a Certificate
    *   sudo certbot --nginx -d example.com -d www.example.com
    *   enter valid email address and accept the terms.
10. Run the java application in EC2 and check the URL