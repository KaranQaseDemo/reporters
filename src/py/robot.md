# Robotframework

Robot Framework is a generic test automation framework for acceptance testing and acceptance test-driven development. It is a keyword-driven testing framework that uses tabular test data syntax.

With qase-robotframework you can publish the results of your automated test runs to your Qase project using the public API endpoints.

## Installation
To integrate Qase into your project, follow these steps:

### Activate the Robot Framework App
1. To activate the app, go to the 'Apps' section in your workspace, and click on 'Activate'.
2. Switch to the 'Access tokens' tab, and create a new API token from here. Save the API token, as we’ll need it in the following steps.

### Add qase-robotframework to your project
To install the reporter, run the following command in a virtual environment 🔗:

```bash
pip install qase-robotframework
```

Add a configuration file for the reporter

At the very least, the reporter will need two variables defined – your Robot Framework App’s Token, and the Qase Project you want to publish the results to:

Ensure that this file is placed in the root of your project.

```
{
  "debug": false,
  "testops": {
    "api": {
      "token": "<app-token>"
    },
    "project": "<project-code>"
  }
}
```

Please refer to [this article](https://help.qase.io/en/articles/9787250-how-do-i-find-my-project-code) for guidance on how to find your Project code in Qase.
<br>

**Let’s verify the integration**, we’ll use a simple test to check if the results are being published to your Qase project. Create a tests/ directory in the root of your project and add the following test:

```
*** Test Cases ***
Simple Addition Test
    ${result}=    Evaluate    1 + 1
    Should Be Equal    ${result}    2
```

Now, let’s run the test by executing the following command:

```
QASE_MODE=testops robot --listener qase.robotframework.Listener ./tests/test_addition.robot`
```

In the above command, we’re setting the reporter’s mode to ‘testops’ using the Environment variable QASE_MODE. You can learn more about other reporter modes here.

Click on the link printed by qase-robotframework to go to the test run in Qase.

<br>
<div style="text-align: center;">
    <img src="./pictures/robot-run_link.png" alt="Test run link" style="width:90%;" />
</div>
<br>

![Test run page](./pictures/robot-run_page.png)


## Configuration

The qase-robotframework reporter can operate in two modes:

	•	Testops: publishes the report to the specified Qase Project.
	•	Report: generates a JSON report locally in the specified directory.

In the next page, we'll take a look at all the available configuration options. These options are common to all our reporters in Python.


