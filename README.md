# I Executed The Project - Re-Architecting Web App on AWS Cloud (Re-factoring with AWS)

**This approach is used to boost agility or improve business continuity.
This will help us to easily scale, add new features and better performance of my application**

# SCENARIO

If you have your workload on-prem, you will be faced with these:

- Operational Overhead

- Struggling with uptime & scaling

- Upfront CapEx & regular OpEx

- Manual process/difficult to automate


**All these process will be time consuming and expenses**


# SOLUTION

We will refactor or re-architect using AWS PAAS and SAAS in AWS ans with Iac.

- It is a PayAsYouGo Model
- Flexible and easy in infractructure management


**STACK (frontend)**

BEANSTACK --VM for Tomcat (app server)

Nginx -----LB replacement

Autoscaling for VM scaling 

S3/EFS -- Storage


**STACK (Backend)

RDS instance --database

Elastic cache

Active MQ

Route53

Cloudfront

# OBJECTIVE

Client needs..

- Flexible infrastructure
- No upfront cost
- Iaac
- PASS
- SAAS


# Architecture of the project

**Users will access the URL which will be resolved to an endpoint from Route53. The endpoint will be of Amazon Cloudfront to serve global audience.
The request wull be redirected to App Loadbalancer and it will be forwarded to an EC2 instance where the app will be running which is in autoscaling group...all inside Elastic Beanstalk. 
There will be cloudwatch alarm that will be mornitoring autoscaling group and will scale out and scale in base on requirement. There will be S3 bucket where artifact will be stored and we can deploy from there. For backend, it will access Amazon MQ, Elastic cache and amazon RDS.**


# FLOW OF EXECUTION

- Login to AWS aacount
- Create keypair for beanstalk instance login
- Create Security group for Elasticcache, RDS, ActiveMQ
- Then Create RDS, Amazon Elastic Cache, Amazon Active MQ
- Create Elastic Beanstalk Env.
- Update SG of backend to allow traffic from beanstalk
- Update SG of backend to allow internal traffic
- Login to EC2 instance for DB initializing
- Login to the instance and initialize RDS DB
- Change healthcheck on beanstalk to /login
- Add 443 https listener to ELB
- Build Artifact with backend info
- DEploy artifact to beanstalk
- Create CDN with SSL certificate
- Update entry inn Godaddy DNS zone
- Test URL


**DETAILED EXECUTION STEP COMING SOON**
