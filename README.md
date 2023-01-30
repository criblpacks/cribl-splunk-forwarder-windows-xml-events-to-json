# **Cribl Splunk Forwarder Windows Sysmon/XML Events to JSON**
----

This pack is designed to transform Splunk Windows Sysmon/XML events to JSON, reduce event sizes, be compliant with the Splunk Common Information Model (CIM) and maintain backwards compatibility with:

* Splunk Add-on for Microsoft Windows: https://splunkbase.splunk.com/app/742
* Splunk Common Information Model (CIM): https://splunkbase.splunk.com/app/1621

---
## **Requirements Section**

### **props.conf**

Add the following stanza to a **props.conf** file on the **Splunk search head**: `$SPLUNK_HOME/etc/system/local/props.conf` to override the Splunk Add-On settings for the Windows sources.  The props.conf can also be deployed in a new app using the Splunk deployment server.

```
[source::XmlWinEventLog...]
KV_MODE = auto
priority = 1
```

### **Reloading Splunk configurations**
1. Restart Splunk is the easiest option but people might not want to restart the Search Head.
1. Reload Search Head Config Files via Search: In Splunk run a search ending with **`| extract reload=t`**
1. Reload Search Head Config Files via URL: In Splunk change the URL of **`http://yoursplunksearchhead/en-US/debug/refresh`**, hit return and select the refresh button. Might take a little bit to complete.
1. Clear Search Head Cache via URL: In Splunk change the URL of **`http://yoursplunksearchhead/en-US/_bump`**, hit return and select the refresh button.


---
## **Using The Pack**
To use this Pack, follow these steps:

1. Install the pack
2. Create a Route/Filter to send all Windows Sysmon/XML Events through the Pack

---
## **Release Notes**
---

**1.0.0** - Initial release.

## **Contributing to the Pack**
---
Discuss this pack on our Community Slack channel [#packs](https://cribl-community.slack.com/archives/C021UP7ETM3).

## **Contact**
---
* Email: <david@cribl.io>
* Slack: [david (cribl.io)](https://cribl-community.slack.com/team/U01C35EMQ01)

## **License**
---
This Pack uses the following license: [`Apache 2.0`](https://github.com/criblio/appscope/blob/master/LICENSE).
