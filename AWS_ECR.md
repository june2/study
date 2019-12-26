### Amazon Elastic Container Repository (Amazon ECR) 

1. setup aws credentials 

2. login 
```
$ aws ecr get-login --region region --no-include-email
$ docker login -u AWS -p password https://aws_account_id.dkr.ecr.us-east-1.amazonaws.com
```

3. create docker image
```
$ docker build -t <name> .
```

3. create repo
```
$ aws ecr create-repository --repository-name ubuntu
```

4. tag/push
```
$ docker tag ubuntu:trusty aws_account_id.dkr.ecr.us-east-1.amazonaws.com/ubuntu:trusty
$ docker push aws_account_id.dkr.ecr.us-east-1.amazonaws.com/ubuntu:trusty
```

5. pull
```
$ docker pull aws_account_id.dkr.ecr.us-east- 1.amazonaws.com/ubuntu:trusty
```

6. delete img
```
$ aws ecr batch-delete-image --repository-name ubuntu --image-ids imageTag=trusty
```

7. delete repo
```
$ aws ecr delete-repository --repository-name ubuntu --force
```


-  ref : 
https://docs.aws.amazon.com/ko_kr/AmazonECR/latest/userguide/ECR_AWSCLI.html
