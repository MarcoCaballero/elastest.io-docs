<div class="range range-xs-left">
<div class="cell-xs-10 cell-lg-6 text-md-left inset-md-right-80 cell-lg-push-1 offset-top-50 offset-lg-top-0">
<h2 id="content" class="h1">Deploying ElasTest on Amazon Web Services</h2>
<div class="offset-top-30 offset-md-top-30">
</div>
</div>
</div>

The easiest way to deploy ElasTest is by using our Amazon CloudFormation template. In a few steps by clicking a couple of buttons and filling a form you will have your ElasTest ready to go. If you don't have an AWS account you will need one (follow those [steps](http://docs.aws.amazon.com/AmazonSimpleDB/latest/DeveloperGuide/AboutAWSAccounts.html) to get it).

<h4 class="small-subtitle">1) Go to <a href="https://eu-west-1.console.aws.amazon.com/cloudformation/">AWS CloudFormation dashboard</a> and create a new stack</h4>

<div class="docs-gallery inline-block">
    <a data-fancybox="gallery-1" href="/docs/deploying/images/new_stack.png"><img class="img-responsive img-wellcome" src="/docs/deploying/images/new_stack.png"/></a>
</div>

<h4 class="small-subtitle">2) Select option "Choose a template" and use <a href="https://raw.githubusercontent.com/elastest/elastest-toolbox/master/AWS/cloud-formation-latest.yaml">this YAML file</a></h4>

<div class="docs-gallery inline-block">
    <a data-fancybox="gallery-1" href="/docs/deploying/images/template.png"><img class="img-responsive img-wellcome" src="/docs/deploying/images/template.png"/></a>
</div>

<h4 id="step-3" class="small-subtitle">3) Complete the form shown on the next step with the following information</h4>

| Parameter        | Value                                                          | Details                                                                                                                                          |
| ---------------- | -------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Stack name       | The name of the stack                                          | Elastest is OK                                                                                                                                   |
| DiskSize         | _50G_ should be ok for testing the app                         | In a production ready environment set to 100GB                                                                                                   |
| ElastestPassword | Your password                                                  | Password to access the platform                                                                                                                  |
| ElastestUsername | Your username                                                  | Username to access the platform                                                                                                                  |
| ElastestVersion  | _latest_                                                       | Which version of elastest do you want to launch. **_latest_** version points to the last stable release of ElasTest, so it is always safe to use |
| ElastestMode     | _mini_, _singlenode_                                           | The ElasTest <a href="/docs/#modes">mode</a>
| InstanceType     | The type of machine you want (recommended at least _m4.large_) | Elastest needs resources to run, please be genereous                                                                                             |
| KeyName          | One of your AWS keys                                           | RSA key to access the instance through SSH                                                                                                       |
| SwapSize         | Recommended at least _4G_                                      | The amount of swap memory in GB                                                                                                                  |
| WantJenkins      | true                                                           | Choose wether you want to deploy Jenkins CI with Elastest                                                                                        |
| WantTestLink     | true                                                           | Choose wether you want to deploy TestLink Project Manager with Elastest                                                                          |

<br>

<div class="docs-gallery inline-block">
    <a data-fancybox="gallery-1" href="/docs/deploying/images/conf.png"><img class="img-responsive img-wellcome" src="/docs/deploying/images/conf.png"/></a>
</div>

<div class="range range-xs-center warning-range">
  <div class="cell-xs-2 cell-lg-1" style="text-align: center;"><span class="icon mdi mdi-information-outline warning-span"></span></div>
  <div class="cell-xs-10 cell-lg-11 warning-text"><p><i>If you need to use a specific DNS, you will have to start ElasTest manually</i></p></div>
</div>

<h4 class="small-subtitle">4) Deploy your stack</h4>

No more configuration is needed. Click on **Next** -> **Next** -> **Create**

Your stack status will show _CREATE_IN_PROGRESS_. Wait a few minutes (between 20 ~ 30) until it shows _CREATE_COMPLETE_. Then you can check _Output_ tab to see the URL where you can access your ElasTest dashboard.

<div class="docs-gallery inline-block">
    <a data-fancybox="gallery-1" href="/docs/deploying/images/output_tab.png"><img class="img-responsive img-wellcome" src="/docs/deploying/images/output_tab.png"/></a>
</div>

That's all. When you connect to your ElasTest URL, enter the username and password you declared in the [third step](#step-3). _Happy testing!_

<h3 class="holder-subtitle link-top">ElasTest data</h3>
You can see the Elastest data information <a href="/docs/deploying/ubuntu/#elastestData">here</a>