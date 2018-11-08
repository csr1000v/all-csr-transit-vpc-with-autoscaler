# Step 1 : Launching a Transit VPC Deployment with optional Autoscaling and DMVPN features

[![Click Here to Launch the template](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=AllCSRTransitVPCStack&templateURL=https://s3.amazonaws.com/csr1000vautoscaler-us-east-1/released/cisco-transit-vpc-primary-account.template)

# Step 2: Launching a Spoke Deployment:

[![Click Here to Launch the template](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=AllCSRTransitVPCStack&templateURL=https://s3.amazonaws.com/csr1000vautoscaler-us-east-1/released/spoke-vpc.template)

# Cisco All CSR Transit VPC Solution on AWS Cloud
This repository contains cloudformation templates to deploy All CSR Transit VPC Solution in AWS cloud with support for Autoscaling feature.

The Autoscaling feature brings the ability to:

1] Monitor different performance metrics for CSRs in Transit VPC (such as CPU Utilization, Network In/Out, CSR custom metrics and many more) using AWS Cloudwatch

2] Adjust the CSR capacity (number of CSRs) in Transit VPC based on traffic load in the network. Currently we support only horizontal scaling with minimum capacity of 2 CSRs and maximum of 8 CSRs in Transit VPC.

3] Automated creation and removal of VPN connections to spoke VPCs and on-premise VPN device as CSRs are added and removed from the Transit VPC.

4] Customer can select BYOL or Hourly licenses for the newly added CSRs through autoscaling independent of the license model for initial two transit VPC CSRs

5] Push custom IOS configurations to all the CSRs in Transit VPC through a configuration file

Recommended:

Install autoscaler-cli for easier management of configuration and troubleshooting for autoscaler feature.

## To install into user directory:
```
~:pip install --no-cache-dir --upgrade --user csr_autoscaler_cli
```

## installed cli exec file will be installed here on a mac:
```
~:which csr_autoscaler
/Users/<username>/Library/Python/2.7/bin/csr_autoscaler
```

## usage:
```
~:csr_autoscaler
Usage:
    csr_autoscaler set aws <storage_name> [--profile <profile>] [--region <region>]
    csr_autoscaler set azure storage_name <storage_name> storage_key <storage_key>
    csr_autoscaler save
    csr_autoscaler upload
    csr_autoscaler show settings
    csr_autoscaler show status
    csr_autoscaler show status raw
    csr_autoscaler show config
    csr_autoscaler show config raw
    csr_autoscaler show actions
    csr_autoscaler show watchers
    csr_autoscaler show logs [minutes]
    csr_autoscaler show logs all [<minutes>]
    csr_autoscaler show logs spoke [<minutes>]
    csr_autoscaler config logs rotate [bysize | bytime] <value>
    csr_autoscaler config logs rotate [enabled | disabled]
    csr_autoscaler config logs save_to_cloud [enabled | disabled]
    csr_autoscaler config debug [Debug | Info | Warning | Error]
    csr_autoscaler config ami <ami-id> [BYOL | LicenseIncluded]
    csr_autoscaler config action <action> [enabled | disabled]
    csr_autoscaler config action <action> debouncetime <debouncetime>
    csr_autoscaler config action <action> minvalcnt <minvalcnt>
    csr_autoscaler config watcher <watcher> [enabled | disabled]
    csr_autoscaler config watcher <watcher> period <period>
    csr_autoscaler config watcher <watcher> action <action> threshold <threshold>
    csr_autoscaler config watcher <watcher> action <action> [enabled | disabled]
    csr_autoscaler config watcher <watcher> action <action> basepct <basepct>
    csr_autoscaler config watcher <watcher> action <action> triggerpct <triggerpct>
    csr_autoscaler logs rotate by_size <size>
    csr_autoscaler logs rotate by_time <time>
~:
```

More information on the Autoscaling feature for All CSR Transit VPC Solution on AWS can be found here:
https://www.cisco.com/c/en/us/td/docs/routers/csr1000/software/aws/b_csraws_transitVPC/Deploying_Autoscaler_for_AWS.html
