---
uid: repair-uninstall-troublesht-agent
---

# Repair, uninstall or troubleshoot a PI to OCS Agent

Enhancements and bug fixes for PI to OCS may require that you update both the PI to OCS Agent and the PI System connection. Since these components work together, updating one usually requires that you also update the other.

The **Details** pane displays the currently installed version of the PI to OCS Agent, and also indicates if you need to update it to the latest version. 
 
![ ](../images/agent-update-message.png "The Agent version update message")

_Agent version update message_

You should update your agent to the latest version if you see the message above. Updates are required for backward compatibility and when the version of the agent installed is older than the version of the PI System connection.

The PI to OCS Agent is updated by downloading a new version of the setup kit and installing the new kit. However, some updates might require uninstalling the agent and reconfiguring both your PI System connection and your data transfer. Specific details about the updates will be communicated by posts in the [OCS Services Blog](https://cloud.osisoft.com/blogs), which is accessed from the OCS main menu.