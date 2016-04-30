# sonar-slack-pusher

[![Build Status](https://travis-ci.org/andnyb/sonar-slack-pusher.svg)](https://travis-ci.org/andnyb/sonar-slack-pusher)

Jenkins plugin for pushing Sonar quality gate statuses to a given Slack channel.

The plugin runs as a post build action and runs no matter the outcome of the job. The plugin makes an API request to
a Sonar server instance to get all the metrics for a given job. If the sonar job has a quality gate defined and
linked to the project all the check given checks will be reported back if they 'fail'.

For a failed quality gate check it looks like this:

**Sonar job**
**Job:** _My project_
**Branch:** _master_

**DANGER**
**Reason:**
- _Coverage < 60_
- _Skipped unit tests > 0_
- _<another failed gate>_

### Configuration

Parameter | Usage | Examples
--------------- | -------------------------- | --------
Slack hook|This is the hook into a given channel and it is generated by the Slack incoming Webhook extension. Just paste the full URL here.|https://hooks.slack.com/services/12/34/56
Additional channel|The default channel can be overridden by entering a given channel name.|'team-spawn'
Sonar root URL|This is the root of the remote Sonar installation. The URL is the base for the metrics query and linkage to jobs.|sonar.mycompany.com:9000
Sonar job name|The name the project has in Sonar. Case sensitive|'super-awesome-service'
Branch name|The name the project has in Sonar is usually post-pended with a branch name e.g. 'JobName Branch'. Set the branch name to find the correct
job. Case sensitive.|'bugfixBranch'
User name|If you need to authenticate against the SonarQube server.|'username'
User password|If you need to authenticate against the SonarQube server.|'********'
