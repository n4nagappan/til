# Send commands to ec2 instances using AWS SSM

1. Follow the instructions [here](http://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-access.html) to create an ec2 role with SSM enabled

2. Attach the IAM role to your ec2 instance from instance settings

3. Install SSM agent on your machine:   
```    
#!/bin/bash
cd /tmp			
wget https://s3.amazonaws.com/ec2-downloads-windows/SSMAgent/latest/debian_amd64/amazon-ssm-agent.deb
sudo dpkg -i amazon-ssm-agent.deb
sudo systemctl enable amazon-ssm-agent
```

4. Get instances that can receive commands : ```  aws ssm describe-instance-information ```
5. Execute commands on one of the supported machines :    
``` 
aws ssm send-command --document-name "AWS-RunShellScript" --parameters commands=["echo helloWorld123>>/tmp/del.txt"] --targets "Key=instanceids,Values=i-066880d88e206cf2e" 
```
