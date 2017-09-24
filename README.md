ansible-aws-snapshot-tool for Debian/Ubuntu
============

Ansible role for installing [aws-snapshot-tool](git@github.com:haikulab/aws-snapshot-tool.git) on the system.

## Overwrite Default Variables

The `vars/main.yml` file should contain your list of packages you want to install in order to override defaults found in `defaults/main.yml`.

## Using AWS SNS Notification Service

If you are planning on using this service please make sure to:

1. Assign correct SNS access permissions (**write** or **AmazonSNSFullAccess**)

If you fail to do this, the script will fail like so:

```
Traceback (most recent call last):
  File "/opt/aws-snapshot-tool/makesnapshots.py", line 235, in <module>
    sns.publish(sns_arn, message, 'Finished AWS snapshotting')
  File "/usr/local/lib/python2.7/dist-packages/boto/sns/connection.py", line 290, in publish
    return self._make_request('Publish', params, '/', 'POST')
  File "/usr/local/lib/python2.7/dist-packages/boto/sns/connection.py", line 765, in _make_request
    raise self.ResponseError(response.status, response.reason, body)
boto.exception.BotoServerError: BotoServerError: 403 Forbidden
{"Error":{"Code":"AuthorizationError","Message":"User: arn:aws:iam::104767170405:user/aws-snapshot-tool is not authorized to perform: SNS:Publish on resource: arn:aws:sns:ap-southeast-2:104767170405:aws_automatic_snapshots","Type":"Sender"},"RequestId":"0de5fb3b-5ef2-575c-b009-a97a219bc70f"}
```

All this means that the script failed to authenticate with AWS SNS service.
