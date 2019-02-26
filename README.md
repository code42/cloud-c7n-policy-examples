# Purpose

This repo is meant to house some example Cloud Custodian policies that are in use by Code42 as of this writing. While we hope these examples drive value for you and your organization, it is important to note that these policies may need to be tuned to your specifc environments needs. We are not currently accepting PRs at this time but wanted to share with the community.

## USE

It is important to understand how the Cloud Custodian works, please refer to the documentation in the support resources section, specifically the `getting started` guide and the `code42 custodian blog post` may be the most helpful if this is new material.

Once you're ready for policies, you may clone this repo and begin working with the contents! Note, these policies will need to be tuned to your specific needs, they are not applicable or tuned for all enviroments.

Some specific callouts to make it easier to work with these files:

### Variables

There are several variables that are capitalized throughout, some include `MESSAGEQUEUENAME, BUCKETNAME, and REQUIREDTAGS` These should be substituted and variablized to your environment needs.

### Custodian Logging/Metrics

`execution-options:output_dir: s3://BUCKETNAME/CustodianLogs/{account_id}/`
This specific option is used to send the cusotdian run log and resources log to an s3 bucket. The data in the s3 bucket may be ingested by SIEM or other tools for customized metrics and data visualization.

Note, there are other ways to ingest these files that can be found in the `custodian reporting features` link below

### Slack integration
`to: ["slack"]`
Here you can see the configuration in how we use SQS to send to directly to SLACK. This actually sends the content of the "resources.json.gz" file directly into a slack channel. This option requires you to create a message queue that is used by the Custodian to send to slack. We speak more about the logs/metrics file contents in our blog post below.

## Support Resources

* [official cloud custodian repo](https://github.com/cloud-custodian/cloud-custodian)
* [official cloud custodian docs](https://www.capitalone.io/docs/index.html)
* [cloud custodian getting started](https://www.capitalone.io/docs/quickstart/index.html)
* [custodian reporting features](https://www.capitalone.io/docs/quickstart/usage.html)
* [official code42 github](https://github.com/code42)
* [code42 custodian blog post](https://tbd.com)