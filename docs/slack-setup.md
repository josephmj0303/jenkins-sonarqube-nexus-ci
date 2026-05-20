# Slack Notification Setup #

## Overview

Slack notifications are used to send Jenkins build status updates for every pipeline execution.  
This helps the team quickly track success, failure, and deployment-related events.

---

## Prerequisites

- A Slack workspace
- A target channel such as `#jenkins-ci`
- Jenkins Slack Notification Plugin installed
- Slack Incoming Webhook or Jenkins Slack app credentials configured

---

## Jenkins Plugin Setup

Install the following plugin in Jenkins:

- **Slack Notification Plugin**

After installation, restart Jenkins if required.

---

## Slack Credentials Setup

In Jenkins, add Slack credentials using one of the supported methods:

- **Secret Text** for a Slack webhook URL
- Or configure a Slack app token if your setup uses token-based authentication

Use a clear credential ID such as:

```text
slack-token
```
Pipeline Configuration

The Jenkinsfile sends notifications in the post { always { ... } } block so the message is posted for both success and failure cases.

Example:
```
def COLOR_MAP = [
    'SUCCESS': 'good',
    'FAILURE': 'danger',
]

post {
    always {
        slackSend channel: '#jenkins-ci',
            color: COLOR_MAP[currentBuild.currentResult],
            message: "*${currentBuild.currentResult}:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\nMore Info at: ${env.BUILD_URL}"
    }
}
```
## Notification Behavior

Build Result	Slack Color	Purpose
SUCCESS		good		Indicates pipeline completed successfully
FAILURE		danger		Indicates pipeline failed and needs attention

## Message Details

Each Slack message includes:

* Build result
* Job name
* Build number
* Jenkins build URL

This makes it easy to open the exact build and review logs immediately.

## Verification

To verify Slack notifications:

* Run the Jenkins pipeline.
* Check the selected Slack channel.
* Confirm that a message appears after build completion.
* Validate both success and failure notifications.
