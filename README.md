# jenkins

Phase 3 of the Infrastructure Automation project

In this phase I'm going to configure Jenkins and its related plugins or services such as ECR and Maven.

Making a fresh new enviroment is the key for a clean start.
I downloaded and installed java and jenkins.
![jenkins](https://github.com/PartySlayer/jenkins-maven/assets/120326157/6c3a4ffa-ce00-4881-9866-31ca1b934849)

Then the page asking for the adminpassword showed up on localhost:8080.
![jenkins1](https://github.com/PartySlayer/jenkins-maven/assets/120326157/e860aa58-4c7f-438b-965a-86258a7e7f03)

Following a fast setup...
![jenkins2](https://github.com/PartySlayer/jenkins-maven/assets/120326157/8a24b2fb-0cfd-4995-9ec9-d24f19fa8101)

...it was time to install the plugins.
![jenkins3](https://github.com/PartySlayer/jenkins-maven/assets/120326157/dffc536c-242f-40ae-b6cc-528bbb1706cf)

After connecting it to EC2, jenkins was operative:
![jenkins4](https://github.com/PartySlayer/jenkins-maven/assets/120326157/a3b8339f-2ef3-4fee-9e8b-d669720ca110)


Now, to enable continuous delivery and deployment it was needed to integrate docker with jenkins.
The goal was to automate the process of creating docker images and pushing them to ECR.

So I added jenkins user to the Docker group.
Then I restarted jenkins, docker and reloaded the system daemons.
![jenkins5](https://github.com/PartySlayer/jenkins-maven/assets/120326157/69e30a41-2ccd-4fd1-97e1-c8eccfeda949)

Back to jenkins, I configured its aws credentials, in order to refer to them in the pipeline like this:
withAWS(credentials: 'phase3', region: 'eu-west-3')
![jenkins6](https://github.com/PartySlayer/jenkins-maven/assets/120326157/e6247160-588a-4197-8f50-1fe578728ce7)

At this point was time to create a repository in ECR,
![jenkins7](https://github.com/PartySlayer/jenkins-maven/assets/120326157/d02da01a-d5ab-4d0e-8d8b-0306238d1420)

and add Maven.
![jenkins8](https://github.com/PartySlayer/jenkins-maven/assets/120326157/de9757a0-4694-4046-93e5-efb4bbdfefa3)

Finally, I could push images on ECR and refer to the maven installation as 'maven' in the pipeline.
tools {
    maven 'maven'
}



