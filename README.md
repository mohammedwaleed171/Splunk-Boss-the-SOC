# Splunk | BOSS the SOC

## Data Set
-In this exercise, you assume the persona of Alice Bluebird, the analyst who successfully assisted Wayne Enterprises and was recommended to Grace Hoppy at Frothly (a beer company) to assist them with their recent issues.
<p align="center"><img src="https://assets.tryhackme.com/additional/splunk-overview/splunk-botsv2-frothly.png" height="40%" width="40%" /><p/></p> <br/>

##  100 series questions 
- The first objective is to find out what competitor website she visited.
- When it comes to HTTP traffic, the source and destination IP addresses should be recorded in logs. We need Amber's IP address.
```index="botsv2" sourcetype="pan:traffic" amber```
<p align="center"><img src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*pS3pqTYHSidwFNfTxDvNUA.png" height="40%" width="40%" /><p/></p> <br/>
- After adding it to the search and changing source type to HTTP and to remove duplicate entries and one to list as a table, we will be using "dedup" and "table" keywords from the ![Splunk Documentation - Search Reference](https://docs.splunk.com/Documentation/Splunk/latest/SearchReference/Metadata) . Final query would be:
  ```index="botsv2" sourcetype="stream:HTTP" "10.0.2.101" | dedup site | table site```
<p align="center"><img src="https://miro.medium.com/v2/resize:fit:828/format:webp/1*xdzUcxFxgoNi99AorCKYDg.png" height="40%" width="40%" /><p/></p> <br/>

**1 — Amber Turing was hoping for Frothly to be acquired by a potential competitor, which fell through, but visited their website to find contact information for their executive team. What is the website domain that she visited?**<br/>
```Answer:www.berkbeer.com```
**2 — Amber found the executive contact information and emailed him. What image file displayed the executive’s contact information?** <br/>
- To answer this, we can query using the below,
  ```index="botsv2" sourcetype="stream:HTTP" "10.0.2.101" berkbeer.com```
  <p align="center"><img src="https://miro.medium.com/v2/resize:fit:786/format:webp/1*ftPOple9iJu7nMdaaXxOHQ.png" height="40%" width="40%" /><p/></p> <br/>
```Answer:/images/ceoberk.png```

- To find Amber's email, we use the below query,
  ```index="botsv2" sourcetype="stream:smtp" berkbeer.com```
  <p align="center"><img src="https://miro.medium.com/v2/resize:fit:720/format:webp/1*yKR3vDIM3wNbaHWNEVVrIw.png" height="40%" width="40%" /><p/></p> <br/>
- We found Amber’s email. Now we can add that to our search,
  ```index="botsv2" sourcetype="stream:smtp" berkbeer.com "aturing@froth.ly"```

**3 — What is the CEO’s name? Provide the first and last name ?** <br/>


