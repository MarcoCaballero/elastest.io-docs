<div class="range range-xs-center">
<div class="cell-xs-10 cell-lg-6 text-md-left inset-md-right-80 cell-lg-push-1 offset-top-50 offset-lg-top-0">
<h2 id="content" class="h1">What is ElasTest?</h2>
<div class="offset-top-30 offset-md-top-50">
<p>ElasTest is a platform aimed to ease end to end (e2e) testing of distributed systems. One of the key features of the platform is the ability to show and analyze logs and metrics of all elements involved in an end to end test.</p><p>For example, suppose a typical three tier web application with a database. A basic e2e test has the following components: the test itself, web browser, web application and database. All those elements can generate logs and metrics of several types (CPU, memory, network packets…). When a test is executed using ElasTest, the tester can see all that monitoring information in the same graphical user interface and with advanced analysis features. 
</p>
<blockquote>WARNING: ElasTest is currently in active development. This means that new features are constantly being added and unexpected bugs may appear.</blockquote>
</div>
</div>
<div class="cell-xs-10 cell-lg-6 cell-lg-push-2"><img src="./images/portfolio-80-420x280.jpg" width="960" height="540" alt="No documentation yet" class="img-responsive reveal-inline-block offset-top-10"></div>
</div>

<h2 class="h3 no-border">ElasTest main features</h2>

<h2 class="h3 no-border">ElasTest core concepts</h2>

<p>
ElasTest is built around three main elements:
<ul>

<li style="margin-top: 30px">
    <strong>SuT</strong> (<i>Software under Test</i>): the tested software itself. At the moment, all SuTs must be provided in the form of a Docker container. Dockerized SuT can be specified in two different ways:
    <ul>
        <li><i>Docker image</i>: SuT is packaged as a single docker image. The name of the image must be specified. If the docker image is not located in DockerHub, then the image name contains the FQDN of the registry.</li>
        <li><i>Docker compose</i>: SuT is composed by several containers and is defined with a <i>docker-compose.yml</i> file.</li>
    </ul>
</li>

<li style="margin-top: 30px">
    <strong>TJob</strong> (<i>Test Job</i>): test to be executed against a piece of software (SuT). In a TJob several things have to be specified:
    <ul>
        <li><i>Environment needed to execute the tests</i>: This is defined with a docker image that contains all tools used by the tests.</li>
        <li><i>How to retrieve and execute the tests</i>: Specified as a set of commands written in bash that will be executed inside the environment defined before (docker container).</li>
        <li><i>The SuT against which tests are executed</i>: That is, the SuT description. If the Sut is already deployed, it is necessary to specify how to reach it (usually with its IP). If the SuT lifecycle is managed by ElasTest, ElasTest needs to know how to deploy and undeploy the SuT. At the moment, a SuT’s docker image can be specified in this case.</li></br>
    A TJob can be executed several times. That can be useful, for example, because SuT has changes and we want to verify that old features are still working. Or if we add more tests to the same TJob test repo, we can execute them against the SuT.
    </ul>
</li>

<li style="margin-top: 30px">
    <strong>TSS</strong> (<i>Test Support Services</i>): services offered by ElasTest to ease the execution and analysis of TJobs. At the moment, only <strong>web browsers</strong> are provided, but in the near future ElasTest will offer mobile devices emulators, IoT devices, security services, Big Data services, WebRTC testing capablities...
</li>

</ul>

<blockquote>
These three elements are the core concepts of ElasTest platform and they are also the <strong>components targeted</strong> by ElasTest platform.
<br>
In other words: <strong>SuT's, TJob's and TSS's are the modules that ElasTest can monitore and analyse for you</strong>. You can gather information and check logs and metrics for any SuT, TJob or TSS. To learn more check <a href="/docs/monitoring">Monitoring</a> section.
</blockquote>

</p>

<h2 class="h3 no-border">ElasTest technologies</h2>

<!---
 Script for open external links in a new tab
-->
<script type="text/javascript" charset="utf-8">
      // Creating custom :external selector
      $.expr[':'].external = function(obj){
          return !obj.href.match(/^mailto\:/)
                  && (obj.hostname != location.hostname);
      };
      $(function(){
        $('a:external').addClass('external');
        $(".external").attr('target','_blank');
      })
</script>