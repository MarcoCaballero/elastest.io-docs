<div class="range range-xs-left">
<div class="cell-xs-10 cell-lg-6 text-md-left inset-md-right-80 cell-lg-push-1 offset-top-50 offset-lg-top-0">
<h2 id="content" class="h1">Parameterized tests</h2>
<div class="offset-top-30 offset-md-top-30">
</div>
</div>
</div>

ElasTest provides a simple way of defining parameters that will be available on both your SuTs and TJobs as environment variables.

Add parameters to a SuT when creating/editing it:

<div class="docs-gallery inline-block">
    <a data-fancybox="gallery-1" href="/docs/testing/images/parameterized/sut_parameters.png"><img class="img-responsive img-wellcome" src="/docs/testing/images/parameterized/sut_parameters.png"/></a>
</div>

Add parameters to a TJob when creating/editing it:

<div class="docs-gallery inline-block">
    <a data-fancybox="gallery-1" href="/docs/testing/images/parameterized/tjob_parameters.png"><img class="img-responsive img-wellcome" src="/docs/testing/images/parameterized/tjob_parameters.png"/></a>
</div>

Just before running a TJob, a dialog will show the parameters and their current values for both the SuT and the TJob. You can check them, edit them and add new ones before running the TJob.

<div class="docs-gallery inline-block">
    <a data-fancybox="gallery-1" href="/docs/testing/images/parameterized/configure_params.png"><img class="img-responsive img-wellcome" src="/docs/testing/images/parameterized/configure_params.png"/></a>
</div>

Parameterizing SuTs and TJobs can give you great advantages. If you are testing an application that makes use of any environment variable, you can easily change its value before running a TJob. And if you actively configure your test code to use environment variables as control mechanisms, it will only take you a couple of clicks in ElasTest to run the same test with different configurations. Let's see how this is reflected in real code in our tests:


<div class="badges-menu noselectionable">
    <span id="java-test-btn" class="badge badge-default my-badge selected">Java</span>
    <span id="js-test-btn" class="badge badge-default my-badge my-badge-disabled">JS</span>
</div>

<div id="java-test" class="testExample lang-section">

<div class="row" style="margin-top: 40px">

<div class="col-md-6">
<pre>
<code class="java">
public class MyTest {

  @Test
  public void test() throws Exception {
      
    String MY_CUSTOM_PARAM = System.getenv("MY_CUSTOM_PARAM");
    boolean enterIf = Boolean.parseBoolean(MY_CUSTOM_PARAM);

    if (enterIf) {

        // Do something in your test

    } else {

        // Do something different in your test

    }
  }

}
</code>
</pre>
</div>

<div class="col-md-6">
    <p>This test is implemented with <strong>JUnit</strong>. It calls <code>System.getenv</code> method to get the parameter "MY_CUSTOM_PARAM". Depending on its value, our test can perform some actions or others.</p>
</div>

</div>
</div>


<div id="js-test" class="testExample lang-section" hidden>
<div class="row" style="margin-top: 40px">

<div class="col-md-6">
<pre>
<code class="javascript">
var chai = require("chai");

describe("My application", () => {
  it("should do something", async function() {

    var MY_CUSTOM_PARAM = process.env.MY_CUSTOM_PARAM;

    if (MY_CUSTOM_PARAM === "true") {

        // Do something in your test

    } else {

        // Do something different in your test

    }
  })
});
</code>
</pre>
</div>

<div class="col-md-6">
    <p>This test is implemented with <strong>mocha</strong>. It accesses <code>process.env</code> property to get the parameter "MY_CUSTOM_PARAM". Depending on its value, our test can perform some actions or others.</p>
</div>

</div>
</div>

<!-- ********************* -->
<!-- ****** Scripts ****** -->
<!-- ********************* -->

<script>
$('#java-test-btn').click(function(event) {
  activateBadge('java-test');
});
$('#js-test-btn').click(function(event) {
  activateBadge('js-test');
});

function activateBadge(sectionName) {
  var disabledClass = 'my-badge-disabled';
  var selectedClass = 'selected';
  
  $('.testExample').hide();
  $('#' + sectionName).show();
  
  // Disable current selected
  $('.selected').addClass(disabledClass);
  $('.selected').removeClass(selectedClass);
  
  // Select clicked
  $('#' + sectionName + '-btn').addClass(selectedClass);
  $('#' + sectionName + '-btn').removeClass(disabledClass);
}

window.onload = function() {
      activateBadge('java-test');
}
</script>


