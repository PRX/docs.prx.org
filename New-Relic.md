New Relic is used to monitor the health of our systems, including applications and servers. The primary New Relic account has been switched entirely to the new Alerts system.

## Availability Monitoring

All availability monitoring is handled through New Relic Synthetics on the primary PRX account, even for apps that are monitored on PRX Lite, and applications that are not otherwise monitored through New Relic.

## Alert Policies

Policies for each domain are broken down into two groups: Major and Minor. Monitoring conditions that are considered to be critical or high-priority belong to the Major group, and all other conditions belong to the Minor group.

In general, downtime (monitored by Synthetics) is considered critical. Error rate conditions are generally not considered critical. Server conditions (memory or disk usage, etc) is handled on a case-by-case basis, based on the importance of the applications running on the hardware.

## Notification channels

All Major group policies belong to a Major Issues channel, and all Minor group policies belong to a Minor Issues channel. There are corresponding Slack channels that are configured to receive notifications from each channel.

Individual users should opt into any notification channels for which they wish to receive alerts. There is generally no need for a user to receive Minor policy notifications.