
## Using ESS in a TJob
A normal TJob simply contains the code for executing a test (e.g. executing a selenium test using a web browser provided by the EUS). Once the test has dinished executing, the program returns and the TJob execution is completed. For scan a TJob using ESS, the author of the TJob must add the following steps before exiting.
1. read the value of the *ET_ESS_API* environmental variable to get the URL of the ESS API. The following is an example (in Python) of how this can be done.
```
import os
ess_api_url=os.environ['ET_ESS_API']
```
2. send a HTTP POST request to the path */ess/api/r4/start/* of the ESS API with a JSON body containing the key *sites* with the value being a list of SuT URLs that needs to be scanned for security. The following is an example (in Python) of how this can be done.
```
import requests
resp=requests.post(ess_api_url+"/ess/api/r4/start/",json={"sites": ["https://example.com"]})
```
3. check whether the ESS scan has completed before exiting
```
if "starting-ess" in resp.text:
            resp=requests.get(ess_api_url+'/ess/api/r4/status/')
            status=resp.text
            while ("not-yet" in status):
                time.sleep(5)
                resp=requests.get(ess_url+'/ess/api/r4/status/')
                status=resp.text
```
We have created the docker image of similar TJob and it's code is available [here](https://github.com/avinash-sudhodanan/sample-ess-tjob/blob/master/fteaching-tjob.py). The docker image is available at
> dockernash/test-tjob-ess

## Executing an ESS security scan for a TJob
1. Visit ElasTest GUI in a Web Browser (see example image shown below)
![][Load TORM]
2. Click on the **New Project** button to create a new project (see example image shown below)
![][Create New Project ]
3. Provide a new for the project (see example image shown below)
![][Fill New Project Details]
4. Click on the **New TJob** button to create a new TJob (see example image shown below)
![][Click New TJob]
5. Configure the TJob by providing the details of the docker image of the TJob created (see example image shown below)
![][Configure TJob]
6. Check the checkboxe corresponding to ESS and other requires TSSes (see example image shown below)
![][Check ESS]
7. Click on the play button to run the TJob (see example image shown below)
![][Run TJob]
8. Scroll down to the iframe the ESS GUI is displayed (see example image shown below)
![][Scroll Down to ESS]
9. Wait until the GUI changes to starting the ESS scan (see example image shown below)
![][Start ESS Scan]
10. Notice the progress bar that indicates the progress of the test and the progress status message displayed above (see example image shown below)
![][Completing ESS Scan]
11. Wait until the scan is complete (see example image shown below)
![][Wait to Finish]
12. Click on an alert to expand it (see example image shown below)
![][Expand Each Alert]
13. Scroll up and click on the name of the TJob to go to the TJob menu (see example image shown below)
![][Click to Go Back To TJob]
14. Click on the last TJob execution (see example image shown below)
![][Click on Exected TJob]
15. Look for the *report.json* file that contains the JSON report of the test (see example image shown below)
![][Click on JSON Report]
16. Click on the button next to it to open the JSON report in a new tab (see example image shown below)
![][View JSON Report]

[Load TORM]: ../images/ess/0.png
[Create New Project ]: ../images/ess/1.0.png
[Fill New Project Details]: ../images/ess/1.1.png
[Click New TJob]: ../images/ess/2.png
[Configure TJob]: ../images/ess/3.png
[Check ESS]: ../images/ess/4.png
[Run TJob]: ../images/ess/5.0.png
[Scroll Down to ESS]: ../images/ess/6.0.png
[Start ESS Scan]: ../images/ess/6.1.png
[Completing ESS Scan]: ../images/ess/6.2.png
[Wait to Finish]: ../images/ess/6.3.png
[Expand Each Alert]: ../images/ess/6.4.png
[Click to Go Back To TJob]: ../images/ess/7.png
[Click on Exected TJob]: ../images/ess/7.1.png
[Click on JSON Report]: ../images/ess/7.2.png
[View JSON Report]: ../images/ess/8.png
