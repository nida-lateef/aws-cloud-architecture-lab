# Lab 1: Amazon S3 Bucket Basics

## Objective

Learn the basics of Amazon Simple Storage Service (Amazon S3), including bucket creation, object upload, deletion, and access security.

## AWS Service

- **Service:** Amazon S3
- **Region:** Asia Pacific (Sydney) — `ap-southeast-2`
- **Lab type:** Hands-on practical exercise

## Tasks Completed

1. Created an S3 general-purpose bucket.
2. Uploaded a test file to the bucket.
3. Deleted the test file.
4. Uploaded the test file again.
5. Checked the bucket's Permissions tab and confirmed that Block all public access was enabled.

## Security Configuration

- Kept public access blocked.
- Did not intentionally make the bucket or its objects public.
- Used a test file rather than sensitive information.

## What I Learned

- An S3 bucket stores objects in AWS.
- Objects can be uploaded and deleted through the AWS Management Console.
- S3 permissions and public access settings are important for protecting stored data.
- Cloud resources should be configured securely and monitored for potential costs.

## Verification

The bucket was created successfully, and the test file was deleted and uploaded again. The bucket's Block all public access setting was confirmed to be enabled.

## Project Status

Completed: Basic S3 bucket and object-management exercises.

## Future Improvements

- Practise downloading an object.
- Explore bucket versioning and lifecycle rules.
- Learn about S3 encryption and access policies.
- Review AWS billing and resource cleanup practices.

- ## Additional Security Check

### Default Encryption
- Checked the bucket's Properties tab.
- Confirmed that default encryption uses SSE-S3.
- Learned that Amazon S3 manages the encryption keys for SSE-S3.
- Kept Block all public access enabled.

### Key Learning
Default encryption helps protect objects stored in Amazon S3. Keeping public access blocked helps reduce the risk of unintended public exposure.

## Security Notes
These settings were inspected in the AWS Management Console. No encryption settings were changed during this check.


