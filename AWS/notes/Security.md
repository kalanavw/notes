* Encryption 101
    * TLS/SSL
* KMS Overview (Key Management Service)
    * Manages encryption key for us
    * Fully integrated with IAM
    * Audit KMS key usage using CloudTrail
    * Keys
        * KMS Customer master key
        * Symmetric key (AES 256) - must call API to retrieve
        * Asymmetric (RAS % ECC key pairs)
    * Types of KMS Keys
        * AWS owned- free
        * AWS Managed - free
        * Customer managed- 1$
    * KMS key policies
        * Control access to KMS keys, similar to S3 bucket policies
* AWS Certificate Manager
    - Easily provision, manage, and deploy TLS Certificates
    - Provide in-flight encryption for websites
    - support both public and private
    - automated TLS certificate renewal
    - cannot use ACM with EC2
    - Can be used with
        - ELB
        - Cloud Front Distrubtions
        - APIs on API Gateway
    - API Gateway - Endpoint Types
        - Edge -Optimized: for global clients
        - Regional - Regional users
        - Private - only in VPC
* AWS WAF - Web  Application Firewall
    - Layer 7 is HTTP
    - protect we application from common web exploits
    - Deploy on
        - Application Load Balancer
        - API Gateway  
        - Cloud Front
        - AppSync GrapQL API
        - Cognito user pool
    - Define WEB Acl (Access ControlList)
    - Web ACL are Regional except for CloudFront
    - A rule group is a reusable set of rules that you can add to a web ACL
    - Does not support the NLB
    - Can use Global Accelerator for fixed IP and WAF on the ALB
- AWS Shield : Protect from DDoS attack
  -  DDos: Distributed Denial of Service - many requests at the same time
  -  Free service
  -  protect from attacks such as SYN/UDP floods, Reflection attacks, and other layer 3 & 4 attacks
-  AWS Firewall Manager
  - Manage rules in all accounts of an AWS Organization
  - Security Policy
      - WAF Rules
      - AWS shield advances (ALB CLB NLB Elastic Ip, Cloud Front)
      - AWS Network firewall (VPC Level)
      - Route 53 Resolver DNS Firewall
      - Policies are created at the regional level
- Amazon GuardDuty
  - Intelligent Threat discovery to protect your AWS account
  - Uses ML Algorithms, anomaly detection, 3rd party data
  - One-click enable( 30 days free trial), no need to install software
  - input data includes
      - CloudTrail event logs
      - VPC Flow logs
      - DNS Logs
      - Optional Logs - EKS Logs, RDS & Aurora. EBS, Lambda, S3 Data Events
      - Can protect against CruptoCurrency attacks - (Has a dedicated finding for IT)
- Amazon Inspector
  - Automated Security Assessments
  - For EC2 instances
    - Leveraging the AWS System Manager (SSM) agent
    - analyze against unintended network accessibility
    - analyze the running OS against known vulnerabilities
  - For Container images push to ECR
    - Assessment of pushed container images
  - For Lambda Fucitions
  - Reporting & integrations with AWS security hub
- Amazon Macie
  - Fully managed data security and data privacy service
  - uses ML & pattern matching to discover and protect the sensitive data in AWS
