1: **Securing Your Data Using S3 Encryption**


2: **Managing Access Control**


  **Limiting IAM User Permissions**
  
  
  Identity and Access Management (IAM) directly enables fine-grained access controls. By applying 
  the principle of least privilege, you can assign users with the minimum access and resources required 
  to administer buckets or read/write data. 

  **Restricting S3 Access Using Bucket Policies**
  
  Bucket policies are similar to IAM user policies with the main difference being that bucket policies 
  are attached to S3 resources directly. Bucket policies allow you to be flexible and manage bucket access 
  with fine-grained permissions.

**3 Bucket Versioning**

Misconfiguration Check:

Versioning:
   Ensure bucket versioning is enabled if you need to preserve, retrieve, and restore every version of
   every object stored in your bucket.

  Actions to Check:

  Check the versioning configuration to ensure it is enabled, which helps protect against accidental 
  deletions and overwrites.

**4: Enforcing SSL**

Using SSL is a great way to secure communication to S3 buckets. By default, S3 Bucket data can be
accessed by using either HTTP or HTTPs, which means that an attacker could theoretically MITM 
(Man in the Middle) your requests to S3.
<img width="606" alt="image" src="https://github.com/user-attachments/assets/a725bcc8-8155-43ad-bc69-19a0e8004f1e">

**5: Enhancing S3 Security Using Logging**

S3 bucket access logging is a feature to capture information on all requests made to a bucket, such as PUT, GET, and DELETE actions. 
