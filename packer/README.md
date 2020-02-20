### Preparing a build environment

To build an image you need:

- access to AWS EC2 with VPC and EBS
- an activation key on RHSM that is associated with subscription providing OCP and RHGS repositories (usually the Employee SKU for System Type = Virtual)
- a system with packer and ansible installed

### Configure your build environment

The following items must be _exported_ before launching packer

```
AWS_ACCESS_KEY_ID=<your-aws-access-key>
AWS_SECRET_ACCESS_KEY=<your-aws-secret-key>
AWS_REGION=<your-aws-region>
AWS_AMI=<aws-ebs-rhel-7-ami>
ORG_ID=<your-rhsm-org-id>
ACT_KEY=<your-act-key-with-access-to-ocp-and-rhgs-subs>
VPC_ID=<any-aws-vpc-id-with-internet-access>
SUBNET_ID=<any-subnet-with-internet-access-on-vpc>
INSTRUCTOR_PUB_KEY_FILE=<absolute-path-to-instructor-ssh-pubkey-file>
```
### Launching Packer

```
AWS_AMI=ami-xxxxxx AWS_REGION=us-xxxx-1 AWS_ACCESS_KEY_ID=XXXXXXXXXXXXX AWS_SECRET_ACCESS_KEY=xxxxxxxxxxxxxxxxxxxx ORG_ID=0000000 ACT_KEY=abcdef SUBNET_ID=subnet-xxxxxxx VPC_ID=vpc-xxxxxxx INSTRUCTOR_PUB_KEY_FILE=/absolute/path/to/instructor_key.pub packer build ocp-cns-aio.json
```
