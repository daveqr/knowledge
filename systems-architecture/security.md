# Security

## Security Threat Models

### STRIDE
System for thinking about security threats.

* **S**poofing of user identity
* **T**ampering
* **R**epudiation
* **I**nformation disclosure (privacy breach or data leak)
* **D**enial of service
* **E**levation of privilege

### DREAD
Risk assesment model for rating security threats. Each category is given a rating from 0 to 10. The sum of all ratings for a given exploit should be used to prioritize among different exploits.

* **D**amage - how bad would an attack be?
* **R**eproducibility - how easy is it to reproduce the attack?
* **E**xploitability - how much work is it to launch the attack?
* **A**ffected users - how many people will be impacted?
* **D**iscoverability - how easy is it to discover the threat?

## Security Basics

### Trust
* Trust is not binary
* need to asses
  * risk tolerance
  * criticality of our data
  * how much we need to invest to feel comfortable
* to be formal, can go through a threat and risk modeling process
* DON'T trust the integrity of the request coming from a user's browser
* DON'T trust that upstream services have done the work to make our data clean and save

### Reject unexpected form input

## Resources
[https://martinfowler.com/articles/web-security-basics.html](https://martinfowler.com/articles/web-security-basics.html)