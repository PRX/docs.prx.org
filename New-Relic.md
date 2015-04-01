New Relic is used to monitor the health of our systems, including applications and servers.

## Alert Policies

For important *application*, *key transaction*, and *server* policies, generally a single policy is created for each property. In some cases very closely related properties will share a policy. Usually there won't be anything assigned to the *default policies*.

### Alert Channels

#### Slack

The `#trouble` channel in Slack should receive all critical event alerts. Make sure it is added as an alert channel on any new policies.

#### Email and Mobile

The `Tech Team` alert group should include any technical staff who needs to be aware of system health and performance. This group should be added as an alert channel to all policies. User alert channels will receive all critical event alerts.

Individual users generally decide which policies are received as emails or mobile push notifications. This can be controller at the policy level by admins, though, if necessary.

### Limited Alert Notifications

Normal alert channels (Slack, Groups, and Users) will receive all alerts (i.e., *all critical events*). If there is a need to send only *first critical events* or *downtime events* notifications to some channel, they need to be configured separately from the normal channels.