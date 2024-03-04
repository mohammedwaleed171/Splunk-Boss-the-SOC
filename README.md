# Splunk | BOSS the SOC

## Data Set
-In this exercise, you assume the persona of Alice Bluebird, the analyst who successfully assisted Wayne Enterprises and was recommended to Grace Hoppy at Frothly (a beer company) to assist them with their recent issues.
<p align="center"><img src="https://assets.tryhackme.com/additional/splunk-overview/splunk-botsv2-frothly.png" height="40%" width="40%" /><p/></p> <br/>

##  100 series questions 
- The first objective is to find out what competitor website she visited.
- When it comes to HTTP traffic, the source and destination IP addresses should be recorded in logs. We need Amber's IP address.


```index="botsv2" sourcetype="pan:traffic" amber```
