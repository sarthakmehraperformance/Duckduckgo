# sindhu.subrahmanya
PlanIT Module

**Please find the answers inline:**

Using Apache JMeter with your choice of language and framework, write a performance test script to
Complete the following 3 transactions:
1. Load DuckDuckGo Homepage (https://duckduckgo.com/)
2. Type Suggested Search Term
3. Select Search Term from the suggested Search Box
	**The above transactions have been included in the script along with a complete transaction that provides Overall Response Time.**

The script should iterate all three transactions and cycle through the following search teams picking a different one on each iteration
      **This has been enabled by using CSV Data Set Config element which accesses P_SearchTermParameter values from a file (SearchParameterFile.csv) that is in bin folder. **

The test needs run for 5 minutes and should achieve 30 iterations per minute.
**This has been achieved by considering the following:**
1.	Number of Vusers: 15
2.	Pacing time : 30s (using Flow Control Action Sampler)
3.	Ramp up period : 45s ( 1 user ramps up every 3s)
4.	Total Duration: 5 minutes + 45s of ramp up period => 345 seconds

Each user should be treated as a new user and caching should be handled appropriately
             **1.Same user on each iteration has been disabled.
             2.To handle Cache, HTTP Cache Manager has been added**
 
Please be aware that your script should report times for the different elements of the search process (homepage, suggested search, search)
           **Different transaction controllers have been added for capturing response times of each transaction individually as mentioned above.**

**A test was run adhering to the above conditions:**

**In order to run the test, please place all the attached files in the bin folder of Jmeter.**

DuckDuckGo.jmx is the jmeter file configured for testing the above mentioned scenario.
DuckDuckGo.bat file has been created to trigger a non GUI mode test which has the below command line: jmeter -n -t DuckDuckGo.jmx -j DuckDuckGo.txt -l DuckDuckGo.jtl
DuckDuckGo jtl file gets generated after the test run which can be used to generate HTML report either on Jmeter UI (Tools -> GenerateHTMLReport) or through the command line.

Results of the already executed test is stored in the folder 'ResultsFolder'.

**Additional Questions:**
**You are given a requirement which states “The system should scale to 2000 users”.
What other questions would you need to ask to get enough information to create a workload model. Please rewrite the requirement above so that it testable and more descriptive.**

1.	Is the application already deployed in production or is it a new one planned to go live?
2.	Is 2000 users the peak number of users already observed on the system (if it is deployed in production) or is it the maximum expected? Based on the criticality, it can be decided to test 2x or 3x the expected load to make sure that the application does not break down in case there is a surge in the numbers than expected.
3.	Would 2000 users be the accessing the system all round the clock or is there any predictability on the application load based on days or time (like weekend load, weekdays load etc). If we could predict that based on the production data or the analysis data, we could plan for setting predictive autoscaling.
4.	Critical transactions of the application aimed to be performance tested and a workflow document for the same.
5.	The number of transactions expected per hour (TPH) 
6.	Response time SLAs of APIs if the application has already undergone baseline testing. 
7.	Architecture of the application to monitor each component involved
8.	Time duration available for testing to prioritize the testing modules

**As well as creating a script in a tool to do the performance testing, what other factors would
need to be considered for a performance testing engagement? **

1.	Requirements gathering timeline
2.	Once requirements are gathered, analysis needs to be done on the complexity of the application and estimation of efforts for scripting (based on the tool selected), test executions, test analysis and test reporting should be done considering a certain buffer period in case something goes wrong during the timeline. A certain buffer period for fine tuning the application (fixing the bugs found during performance testing) should also be considered.
3.	Test analysis timeline should be estimated based on the tools available for monitoring the application. 
4.	Based on the application criticality and requirements, decide on the kind of performance testing that needs to be conducted. For eg, load test, stress test, endurance test etc.
5.	Management perspective - making sure that enough resources are available to handle the performance testing engagement. 
6.	Also, it should be considered that the resources working on the project have overlapping time with developers and project stakeholders for better collaboration.
7.	Performance engineering solution should be designed in a way that aligns with Client’s priorities such as Cost optimization, Security, Disaster Recovery etc. If Client is not across these specifications, efforts should be made to deliver a session to help them gain a better understanding of the requirements and then start planning for a performance engineering solution. 

