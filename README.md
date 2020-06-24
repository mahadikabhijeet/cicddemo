# cicddemo
**This is to demonstrate continuous delivery through github actions**
Follow the below task list instructions to create a sample fargate demo pipeline using github actions. The example is setup in `us-east-1` region so if you want to implement in other region then change the regions accordingly.
- [ ] Create an IAM user with appropriate permissiond for creating ECS and ECR. Give it a appropriate `AmazonECSTaskExecutionRolePolicy` having `ecsTaskExecutionRole`. For more details follow the [AWS IAM doccumentation](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_execution_IAM_role.html).
- [ ] Create an And download __AWSAccessKeyId__ and __AWSSecretKey__ and set it up with your aws cli. For doccumentation on how to set AWS CLI click [here](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html).
- [ ] From aws cli create the ECR repository as in the yml file we need some repo to store the docker file image. `aws ecr create-repository --repository-name my-ecr-repo --region us-east-1`
- [ ] Now create a default cluster in ECS from your getting started guide for httpd:2.4 using *sample-app*. Keep the defaults for now so that your action will run without interruption.
- [ ] In the task-definition.json file change the `"executionRoleArn": "arn:aws:iam::541893147748:role/ecsTaskExecutionRole",` with your respective role ARN. To get this after launching the app using fargate service go to task defiantion and in that see the JSON in your console. 
- [ ] In github go to settings -> secrets and add the __AWSAccessKeyId__ and __AWSSecretKey__ `AWS_ACCESS_KEY_ID` `AWS_SECRET_ACCESS_KEY` like this respectively.
- [ ] Now do some changes in task-defiantion.json and then `git add`, `git commit -m "xyz"`, `git push origin manster` to your repo. After this Observe and enjoy your deployments...

I carried out this execution from this post https://aws.amazon.com/blogs/opensource/github-actions-aws-fargate/ . But My job was getting stuck in pending state. So if you need more clarification then follow this doccumentation and also follow github actions doccumentation. For any doubt or suggestion email me at abhijeetmahadik19@gmail.com. Thanks A lot...
