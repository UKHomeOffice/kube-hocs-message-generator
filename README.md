# kube-hocs-message-generator
Kubernetes configuration of the message generator project

## Usage 
The basic drone command is :

```sh
drone1 build promote -p VERSION=branch-epic_HOCS-COMP ukhomeoffice/hocs-message-generator $(drone1 build last ukhomeoffice/hocs-case-creator --format "{{ .Number }}" --branch main) hocs-delta
```

This command will send 1 randomly selected message to the hocs-delta namespace. This should be changed as required.

Without additional parameters the command will create 1 message, with the message being one of the following randomly selected.
* BIOMETRIC
* DECISION
* DELAYS
* EXISTING
* MAKING_APPOINTMENT
* POOR_INFORMATION
* REFUND
* SOMETHING_ELSE
* STAFF_BEHAVIOUR
* SUBMITTING_APPLICATION

There are two additional parameters :

* RUN_CONFIG_NUM_MESSAGES
* RUN_CONFIG_COMPLAINT_TYPE

if RUN_CONFIG_NUM_MESSAGES is set e.g.

```sh
drone1 build promote -p VERSION=branch-epic_HOCS-COMP -p RUN_CONFIG_NUM_MESSAGES=2 ukhomeoffice/hocs-message-generator $(drone1 build last ukhomeoffice/hocs-case-creator --format "{{ .Number }}" --branch main) hocs-delta
```
then 2 random messages will be sent.

If RUN_CONFIG_COMPLAINT_TYPE is set to one of the types above, then that message type is sent. e.g.
```shell
drone1 build promote -p VERSION=branch-epic_HOCS-COMP -p RUN_CONFIG_COMPLAINT_TYPE=STAFF_BEHAVIOUR -p RUN_CONFIG_NUM_MESSAGES=3 ukhomeoffice/hocs-message-generator $(drone1 build last ukhomeoffice/hocs-case-creator --format "{{ .Number }}" --branch main) hocs-delta

```
then 3 staff behaviour complaints will be sent.
