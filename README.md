# icinga2-teams-notification

This is a adaptive version of:
- [REPO](https://github.com/seffparker/icinga2-teams-notification)
Which is based on:
- [slack alert](https://github.com/seffparker/icinga2-rich-slack-notification)

This is trying to get back to be more in line with the slack alerts.

# Limitation / ToDo
Code in markdown seems to be unsupported?


# Preview
![Sample Notification Preview](https://github.com/william-sy/icinga2-adaptive-teams-notification/blob/main/image/preview.png?raw=true "Sample Notification Preview")


# Features
1. Colored Notifications for states like OK, Warning, Critical etc.
1. Includes raw plugin outputs.(known to be broken in adaptice cards)
1. Shows alert state-duration in human readable format.
1. Shows comment with owner for Acknowledgement and Custom notifications.
1. Can send notifications to multiple Teams endpoints
1. The default re-notification interval can be changed.
1. The re-notification interval can be customized per host or service.
1. When the notification for a host is enabled, it will be inherited to all of its services checks, unless disabled for the specific service(s).
1. Emoticons!

# Installation and Basic Configuration
1. Copy the `/configuration/master_*` files to `/etc/icinga2/conf.d/` or `/etc/icinga2/zones.d` directory (depending on architecture)
1. Modify the `vars.teams_notifications_icinga2_base_url` in the `master_teams_config.conf` with your IcingaWeb2 Base URL. This is to jump to Alert Dashboard right from Teams channel.
1. Configure the existing host or service configuration like the provided one in the `/configuration/host_sample.conf`
3. Get the `webhook_url` of the Teams Channel and add in to the `object User` section of required notification user(s). [Read more here](https://docs.microsoft.com/en-us/microsoftteams/platform/webhooks-and-connectors/how-to/add-incoming-webhook)
4. Validate the Icinga2 configuration and restart the service.

# Advanced Configuration
1. The notification color can be changed in the array variable `vars.teams_notifications_color` using the supported card colors [Documentation](https://adaptivecards.io/explorer/Container.html).
1. Notifications for Scheduled DOWNTIME alerts are disabled by default. It can be enabled in the variable `types`
