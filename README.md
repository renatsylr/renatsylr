<<<<<<< HEAD
# GitHub Action: Workflow Run Wait

wait for all `workflow_run` required workflows to be successful

[![license][license-img]][license-url]
[![release][release-img]][release-url]
[![super linter][super-linter-img]][super-linter-url]
[![test][test-img]][test-url]
[![semantic][semantic-img]][semantic-url]

<details>
  <summary><strong>Why?</strong></summary>

The [`workflow_run`](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#workflow_run) event occurs when a workflow run is requested or completed, and allows you to execute a workflow based on the finished result of another workflow.

###### example

``` yaml
on:
workflow_run:
  workflows: [ test ]
  types: 
    - completed
```

However by itself, this doesn't quite work as expected.

1.  The `completed` type, does not indicate success, for that you'd have to include the following in each job of your workflow:

    ``` yaml
    if: ${{ github.event.workflow_run.conclusion == 'success' }}
    ```

2.  If you're depending on more than one workflow, then ANY of them completing, will trigger the event

    ###### example

    ``` yaml
    name: deploy

    on:
    workflow_run:
      workflows: [ test, lint, compile ]
      types: 
        - completed
    ```

    > *if your `test` workflow fails, but `lint` completed successfully, `github.event.workflow_run.conclusion == 'success'` will still be true*

3.  Your workflow will trigger as many times as you have workflow dependencies

        > _in the previous example, our `deploy` workflow, will run 3 times!_

    All this makes the `workflow_run` event fundamentally broken for any advanced usage, this Action aims to remedy that.

    > ***Note**: See this [Community discussion](https://github.community/t/workflow-run-completed-event-triggered-by-failed-workflow/128001/5) for more info on the topic*

</details>

## Usage

``` yaml
on:
  workflow_run:
    workflows: [ test-client, test-server ]
    branches: [ master ]
    types: [ completed ]

jobs:
  xyz:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
      - uses: ahmadnassri/action-workflow-run-wait@v1

      # only runs additional steps if [ test-client, test-server ] were successful
```

### Inputs

| input              | required | default        | description                                     |
|--------------------|----------|----------------|-------------------------------------------------|
| `github-token`     | ❌        | `github.token` | The GitHub token used to call the GitHub API    |
| `timeout`          | ❌        | `30000`        | timeout before we stop trying (in milliseconds) |
| `delay`            | ❌        | `5000`         | delay between status checks (in milliseconds)   |
| `sha`              | ❌        | `github.sha`   | Git SHA, if it's different from `github.sha`    |
| `ignore-cancelled` | ❌        | `false`        | ignore cancelled workflow runs                  |

----
> Author: [Ahmad Nassri](https://www.ahmadnassri.com/) &bull;
> Twitter: [@AhmadNassri](https://twitter.com/AhmadNassri)

[license-url]: LICENSE
[license-img]: https://badgen.net/github/license/ahmadnassri/action-workflow-run-wait

[release-url]: https://github.com/ahmadnassri/action-workflow-run-wait/releases
[release-img]: https://badgen.net/github/release/ahmadnassri/action-workflow-run-wait

[super-linter-url]: https://github.com/ahmadnassri/action-workflow-run-wait/actions?query=workflow%3Asuper-linter
[super-linter-img]: https://github.com/ahmadnassri/action-workflow-run-wait/workflows/super-linter/badge.svg

[test-url]: https://github.com/ahmadnassri/action-workflow-run-wait/actions?query=workflow%3Atest
[test-img]: https://github.com/ahmadnassri/action-workflow-run-wait/workflows/test/badge.svg

[semantic-url]: https://github.com/ahmadnassri/action-workflow-run-wait/actions?query=workflow%3Arelease
[semantic-img]: https://badgen.net/badge/📦/semantically%20released/blue
=======
## Hi there <img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="30px"> Taner Söyler Greets You With His Best Wishes..

           
<p align="center">
 <a href="#"><img src="https://readme-typing-svg.herokuapp.com/?lines=+Hi%2C%20welcome%20to%20my%20GitHub%20page;I%20am%20AWS%20Devops%20Engineer;Solution%20Architect;+5%20years%20of%20IT%20experience;&font=Anton&center=true&width=650&height=120&color=00FF00&vCenter=true&size=45%22"></a>  
</p>
                
  [![](https://img.shields.io/badge/linkedin-%230077B5.svg?&style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/taner-söyler/) 
<a href="https://renatsylr.github.io/" target="_blank"> <img src="https://user-images.githubusercontent.com/94930605/160260064-ff3aa908-cbfd-4350-ab28-a26a0b7a1819.png" alt="github_pages" height="28.5"/></a> <img src="https://komarev.com/ghpvc/?username=renatsylr" alt="visitor counter" width="15%"/>
<!-- <p align="center">  </p> -->

### What I'm using ? 🛠
 
   Amazon Web Services & DevOps Tools are my choices.

 I like constantly learning , improving and sharing as a lifestyle.

💬 Please contact me on LinkedIn to share about anything or produce a collaborative project or for any help I can provide.

 ## :hammer_and_wrench: Skills
 
**AWS; EC2, , Load Balancer ,Auto Scaling, S3, RDS, CloudFormation,  VPC, CloudFront, Elastic Beanstalk, Route 53 **

**PYTHON, LINUX, GIT, GITHUB, GITLAB, VISUAL STUDIO CODE, SLACK **

**DEVOPS; KUBERNETES, DOCKER, TERRAFORM, ANSIBLE, JENKINS, MAVEN, NEXUS, JIRA SOFTWARE **
  
## 🚴 Skills 
<p>
<a href="#" target="_blank"> <img src="https://www.vectorlogo.zone/logos/amazon_aws/amazon_aws-ar21.svg" alt="AWS" width="70" height="48"/> </a> 
<a href="#" target="_blank"> <img src="https://algoteque.com/wp-content/uploads/2019/04/1AwvDJDfErlD34ox2QpwGoA.png" alt="DevOps" width="100" height="48"/> </a> 
<a href="#" target="_blank"> <img src="https://www.vectorlogo.zone/logos/python/python-horizontal.svg" alt="python"  height="48"/> </a> 
<!-- <a href="#" target="_blank"> <img src="https://www.vectorlogo.zone/logos/java/java-ar21.svg" alt="Java"  height="48"/> </a> -->
<a href="#" target="_blank"> <img src="https://www.vectorlogo.zone/logos/linux/linux-ar21.svg" alt="Linux"  height="48"/> </a> 
<a href="#" target="_blank"> <img src="https://www.vectorlogo.zone/logos/git-scm/git-scm-ar21.svg" alt="git"  height="48"/> </a> 
<a href="#" target="_blank"> <img src="https://1000logos.net/wp-content/uploads/2021/05/GitHub-logo.png" alt="github" height="48"/> </a>
<a href="#" target="_blank"> <img src="https://www.vectorlogo.zone/logos/gitlab/gitlab-ar21.svg" alt="gitlab" height="48"/> </a>
<a href="#" target="_blank"> <img src="https://www.vectorlogo.zone/logos/visualstudio_code/visualstudio_code-ar21.svg" alt="vs-code" height="48"/> </a>
<a href="#" target="_blank"> <img src="https://www.vectorlogo.zone/logos/kubernetes/kubernetes-ar21.svg" alt="kubernetes" height="48"/> </a>
<a href="#" target="_blank"> <img src="https://www.vectorlogo.zone/logos/docker/docker-ar21.svg" alt="docker" height="48"/> </a>
<a href="#" target="_blank"> <img src="https://www.vectorlogo.zone/logos/terraformio/terraformio-ar21.svg" alt="Terraform" height="48"/> </a>
<a href="#" target="_blank"> <img src="https://www.vectorlogo.zone/logos/ansible/ansible-ar21.svg" alt="Ansible" height="48"/> </a>
<a href="#" target="_blank"> <img src="https://www.vectorlogo.zone/logos/atlassian_jira/atlassian_jira-ar21.svg" alt="Jira"  height="48"/> </a>
<a href="#" target="_blank"> <img src="https://www.vectorlogo.zone/logos/jenkins/jenkins-ar21.svg" alt="jenkins"  height="48"/> </a>           
<!-- <a href="#" target="_blank"> <img src="https://www.vectorlogo.zone/logos/w3_html5/w3_html5-ar21.svg" alt="html" height="48"/> </a>
<a href="#" target="_blank"> <img src="https://www.vectorlogo.zone/logos/w3_css/w3_css-ar21.svg" alt="css" height="48"/> </a> -->
<a href="#" target="_blank"> <img src="https://www.vectorlogo.zone/logos/slack/slack-ar21.svg" alt="Slack" height="48"/> </a> 
</p>


## 📊 Statistics
<p align="left">
<img src="https://github-readme-stats.vercel.app/api?username=renatsylr&theme=chartreuse-dark&show_icons=true" alt="my github stats" width="49%"/>&nbsp;
<img src="https://github-readme-streak-stats.herokuapp.com/?user=renatsylr&theme=chartreuse-dark&show_icons=true" alt="my commit status" width="49%" /> </p>
<p align="center"> <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=renatsylr&theme=chartreuse-dark&layout=compact" alt="languages" width="50%" > </p>




>>>>>>> e183d4b6fb2edad2fe0b4fb0447f7141910e35f9
