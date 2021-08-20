 ** aws-cli with session-manager plugin  && Terraform
 
 **Docker build**

docker build --no-cache -t tools:1 .

  **Usage**


*SSM:* 

docker run --rm -it -v ~/.aws:/root/.aws -v $(pwd):/aws -e AWS_PROFILE=default tools:1 "aws ssm start-session --target i-abcdefg123456789"

*SSH via SSM:*

docker run --rm -it -v ~/.aws:/root/.aws -v $(pwd):/aws -v ${HOME}/.ssh/id_rsa:/ssh -e AWS_PROFILE=default tools:1 "ssh -i /ssh ec2-user@i-abcdefg123456789"
