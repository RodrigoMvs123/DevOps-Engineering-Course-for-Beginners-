# DevOps-Engineering-Course-for-Beginners-

https://youtu.be/j5Zsa_eOXeY 

https://github.com/webappio/livechat-example 

Course Outline

Unit 1: Code review automation ( Lesson 1-6 )
Unit 2: Deployment strategies ( Lesson 7-11 )
Unit 3: Application Performance Management ( Lesson 12-13 )

Lesson 1 
What is DevOps ?

DevOps Definition 
A methodology that helps engineering teams build products by continuously getting user feedback.

Code
Build 
Test
Release
Deploy
Operate
Monitor 
Plan

DevOps Engineering Definition
Practical use of DevOps within software engineering teams. Been able to build, test, release and monitor applications.

Devops Engineering Pillars 

Pull Request Automation 
Developers share code changes using git tools like GitHub, GitLab and bitbucket 
A set of code changes in git tools is called a “pull request” or “merge request”
If pull requests are approved, the code changes can go into the main codebase

Git Definition
Git is used for cloud-based code change collaboration. See the full history of code changes, review developer changes, and store code in files called repositories.

The code review

Code style 
Architecture 
Scaling

Product Manager
Engineering Manager 
Designers 
Markets
C-suite

What can be automated ?

Continuous Integration ( CI ) 
Per change ephemeral environments 
Automated Security Scanning
Notifications to reviewers

Goal as DevOps Engineer
Help developers change proposals get reviewed and merged within 24 hours of when they are made.

StackOverflow
“Can you make a build in one step ? ”
https://stackoverflow.com/ 

Deployment Automation
Deploy a feature to a certain set of users as a final test before rolling it out publicly
Starting new versions of services without causing downtime
Rolling back to the prior version in case something does go wrong

Goal as a DevOps Engineer
Have the right tools in place that facilitate deployment without having to have too much custom code
https://spinnaker.io/ 
https://www.harness.io/ 
 
Application Performance Management 
Metrics: numeric measurements of key numbers in production
Logging: text descriptions of what is happening during processing
Monitoring: take metrics and logs to convert them into health metrics
Alerting: If monitoring detects a problem, it notifies developer

Lesson 2
What is Test Driven Development  ( TDD ) ?

Testing 

Test Driven Development Definition 
Known sometimes as TDD, it is a coding methodology where tests are written before code is written.

Unit tests
Integration tests
System ( end to end ) tests
Acceptance tests

TDD Goals
Know when something breaks and where
Know that the whole system is working correctly 

Workflow With TDD
Choose something to work on
Write tests that would pass if product works
Keep building until all tests pass

Lesson 3
What is continuous integration ( CI )  ?

Continuous Integration Definition 
Developers push many small changes to a central git repository per day. These changes are verified by an automatic software that runs comprehensive tests to ensure no major issues  are seen by customers.

Top 3 Benefits of CI : 
CI is the first step to DevOps automation and helps with code collaboration
CI helps improve developer speed without breaking existing code
CI helps reduce customer churn and user satisfaction by preventing broken code from publishing 

GitHub Repository
https://github.com/webappio/livechat-example 
Services
Web
Src 
Views
Main
Main.css

.mainBody .sidebar {
       background: #1c4784;
}

.mainBody .sidebar .mainBody .sidebar .btn {
       color: #85808d;
}

Propose changes
Create Pull Request
Files Changed

Conversation
Pull Requests
Close pull request

Code
Services
cypress
tests
test_chat.js

test_chat.js
describe('The Chat Page', () => {
    beforeEach(() => {
        const username = "testuser"
        const password = "p@ssword"

        const formData = new FormData();
        formData.append('name', 'myuser');
        formData.append('password', 'p@assword');
        cy.request({
            method: 'POST',
            url: '/api/login',
            form: true,
            body: {'name': 'myuser', 'password': 'p@assword'},
        });

        // our auth cookie should be present
        cy.getCookie('default').should('exist');
    })

    it('can send a chat message', function () {
        cy.visit('/');

        let num = Math.random();
        cy.get('.message-area').type(`some message #${num}{enter}`);

        cy.get('.message-wrapper:last-child .message-text').should('have.text', `some message #${num}`)
    })
})

Livechat-example ( Web Application )
…

GitHub Plugin: 
https://webapp.io/ 

LayerCI
Choose a repository 
layerdevopsdemo/livechat-example

Choose a framework
Docker Compose
Build a Layerfile

from vm/ubuntu: 10.04

# Instal docker-ce ( from tutorial for ubuntu ) 
RUN apt-get  update && \
         apt-get isntall apt-transport-https ca certificates curl software-properties-common && \
         curl -FsSl https://download.docker.com/linux/ubuntu/gpg | apt-key add - && \
         add-apt-repository “ deb [arch-and64] https://download.docker.com/linux/ubuntu bionic stable” && \
         apt-get update && \ 
         apt-install docker-ce awscli

# Install docker compose
RUN curl -L “https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s) $(uname -n)” -o/usr/local/bin/docker-compose && |
          chmod -x usr/local/bin/docker-compose

# Copy the root(i.e. repository root) to /root in the runner 
COPY / /root

RUN REPEATABLE docker-compose build - -parallel
RUN docker-compose up -d

RUNRUN docker-compose exec cypress bash /app/run_tests.sh

# BUTTON Shows a button and pauses the pipeline until it is pressed
BUTTON Deploy this pipeline

RUN echo “For AWS the command night look like this:”
RUN echo awscli deploy - -template-file my-file.yaml 
RUN echo “Note that these commands only run if you click the button on the LayerCI dashboard.”

Code
Services
Web 
Src
View
Main
main.css

main.css
html, body {
  padding: 0;
  margin: 0;
  height: 100%;
}

body {
  font-size: 15px;
  font-weight: 400;
  line-height: 1.5;
}

.mainBody {
  width: 100%;
  min-height: 100vh;
}

.mainBody header {
  background: #0c5db8;
}

.mainBody .sidebar {
  background: #1c4784;
  height: auto;
  flex: 0 0 200px;
}

.mainBody .sidebar, .mainBody .sidebar .btn {
  color: #80858d;
}

header {
  color: #fefefe;
}

.mainBody .sidebar .btn.active {
  color: #adb5bd;
}

.mainBody .sidebar .btn {
  padding: 0;
}

.mainBody .sidebar .btn:hover {
  color: #fff;
}

.messages {
  flex: 1 1 auto;
}

.messages-list-container {
  max-height: calc(100vh - 210px);
  overflow-y: auto;
}

.message-area-wrapper {
  border-radius: 5px;
  border: 1px solid #1b1e21;
  width: 100%;
}

.message-area {
  border: none;
  overflow: auto;
  outline: none;

  -webkit-box-shadow: none;
  -moz-box-shadow: none;
  box-shadow: none;
  resize: none;

  width: 100%;
}

.new-channel-lightbox {
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.7);
  justify-content: center;
  align-items: center;
}

.new-channel-modal {
  background: #fff;
  border-radius: 5px;
  border: 1px solid #000;
}

Files changed 
Change color for customer #4
mainBody header {
       background: #50ecb8;
       background: #1c4784;
}

mainBody .sidebar {
       background: #471c84;
       background: #1c45db;
       height: auto;
       flex: 0 0 200px;
}

Change color for customer #4
                                                                                                            Verified . f457da9
                                                                                                                   Details 
https://webapp.io/ Continuous Integration ( CI )

Change color for customer #4
All checks have passed 
This branch has no conflicts with the base branch

Merge pull request 

Lesson 4
What is code coverage ?

Code Coverage Definition
Methodology that quantitatively measures how comprehensive a code base´s tests are. Increasing code coverage often increases stability and reduces bugs.

Branch Coverage Definition ?
A very relevant concept to code coverage is “branch coverage” - instead of measuring how many lines of code, it measures groups of lines.

*.spec.js @engineering-manager-username 

https://about.codecov.io/ 
https://coveralls.io/
https://codeclimate.com/ 

Lesson 5
Linting best practices 

Linting Definition
Linters look at a program's source code and find problems automatically. They are a common feature of pull request automation because they ensures that “obvious” bugs do not make it to production 

https://google.github.io/styleguide/ 

The Nit Approach Definition

Code reviewers leave little comments on the code called “nits” that the team can ignore until broader reviews. Nits are helpful as future references but prevent blocking import changes.

Auto Formatter Definition

Tools that help apply code style rules based on the style guide your team has chosen automatically.

find . -name ‘.go’ -not -path “/vendor/*” -exec gofmt -s -w { } ;

python: pylint, flake8, SonarQube, DeepSource

Lesson 6
Ephemeral environments 

Ephemeral environments Definition
Temporary deployments that have self-contained versions of your application, generally every feature branch.

https://www.heroku.com/
https://webapp.io/

Continuous Staging Definition
CI/CD is merged with ephemeral environments to form a unified CI/CD and review process for every commit.

https://github.com/webappio/livechat-example/blob/main/Layerfile 
Service
Web
…

Lesson 7
VMs vs. Containers

Unit 2
Deployment Strategies

https://www.apache.org/ 
https://www.nginx.com/ 

How containers work
Containers work by creating “namespaces”, which are a linux feature that group shared resources together. For example, if you have five processes running together within a docker container, they had still be running within linux itself.

root@web-6bd6bfc85b-lws8:/# ps aux | wc -l
10

Lesson 8
Running deployments 

Rolling Deployments Definition
Strategy to deploy a new version of an application without causing downtime. They work by creating a single instance of the new version of an application then shutting off one instance of the old version until all instances have been upgraded.

Lesson 9
Blue/green deployments 

Blue/Green Deployments Definition
Strategy to deploy a new version of an application. They work by starting an entirely new instance of the application and then routing traffic over to it.

Code
Services
Web 
Src
View
Main
main.css

main.css
html, body {
  padding: 0;
  margin: 0;
  height: 100%;
}

body {
  font-size: 15px;
  font-weight: 400;
  line-height: 1.5;
}

.mainBody {
  width: 100%;
  min-height: 100vh;
}

.mainBody header {
  background: #0c5db8;
}

.mainBody .sidebar {
  background: #1c4784;
  height: auto;
  flex: 0 0 200px;
}

.mainBody .sidebar, .mainBody .sidebar .btn {
  color: #80858d;
}

header {
  color: #fefefe;
}

.mainBody .sidebar .btn.active {
  color: #adb5bd;
}

.mainBody .sidebar .btn {
  padding: 0;
}

.mainBody .sidebar .btn:hover {
  color: #fff;
}

.messages {
  flex: 1 1 auto;
}

.messages-list-container {
  max-height: calc(100vh - 210px);
  overflow-y: auto;
}

.message-area-wrapper {
  border-radius: 5px;
  border: 1px solid #1b1e21;
  width: 100%;
}

.message-area {
  border: none;
  overflow: auto;
  outline: none;

  -webkit-box-shadow: none;
  -moz-box-shadow: none;
  box-shadow: none;
  resize: none;

  width: 100%;
}

.new-channel-lightbox {
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.7);
  justify-content: center;
  align-items: center;
}

.new-channel-modal {
  background: #fff;
  border-radius: 5px;
  border: 1px solid #000;
}

Files changed 
Change color for customer #4
mainBody header {
       background: #50ecb8;
       background: #1c4784;
}

mainBody .sidebar {
       background: #471c84;
       background: #1c45db;
       height: auto;
       flex: 0 0 200px;
}

Update main.css #8

Propose changes
Create Pull Request
Files Changed

Conversation
Details
LayerCI

Details
Web Application
Login to the Livechat Example
default
…
Merge pull request
                                                         
Lesson 10 
What is auto scaling ?

Auto Scaling Definition
Auto scaling automates horizontal scaling to ensure that the number of workers is proportional to the load on the system.

AWS EC2 Spot Instances
Kubernetes horizontal pod auto scaling

Lesson 11
What is service discovery ?




// within backend, before dns-based discovery:
mongoose.connect(‘mongodb://’+process.env[“MONGODB_IP”]+’:27017/myapp’);

// now with dns-based discovery:
mongoose.connect’mongodb://mongo:27017/myapp’);

Tool Recommendations:

https://coredns.io/ 

Lesson 12
What is log aggregation ?

Application Performance Management 

Log Aggregation Definition 
It is a way of collecting and tapping applications logs from many different services into a single dashboard that can easily be searched.

https://www.elastic.co/pt/logstash 
https://www.fluentd.org/ 
https://www.dynatrace.com/monitoring/platform/comparison/dynatrace-vs-datadog/?utm_source=google&utm_medium=cpc&utm_term=why-dynatrace-dd-st&utm_campaign=br-why-dynatrace&utm_content=none&utm_campaign_id=674205963&gclsrc=aw.ds&gclid=Cj0KCQjw_5unBhCMARIsACZyzS2xpk0q6p7O1QYmK6nAA0P3HeB8IY5AzHtDn1zd0qNiI4tJEDLVnsAaAiKFEALw_wcB
https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html

Lesson 13
Vital Production Metrics

Log aggregation primarily deals with text - logs are textual. In contrast, metric aggregation deals with numbers.

Open Source Metrics Services
Prometheus





