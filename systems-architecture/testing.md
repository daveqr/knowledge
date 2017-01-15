# Testing

## Failure Testing
* Gremlin Inc -- failure as a service
* has an api so that it can be built into deployment pipeline
* https://www.gremlininc.com/
* what's the cost of being down?
* what are steps?

### Testing levels
1. level one just start breaking things (chaos monkey approach)
* level two -- how to break things in prod? something like gremlin
* level three -- running it in prod (even taking one service out)

* running in prod should be end goal
* running failure test at scale in prod

### How to break in new engineers?
* red team blue team strategy
* red team are existing engineers
* blue team new team members
* red team prepares planned outage during business hours which they don't tell blue team about
* gives blue team controlled experience
* red team knows how to back out problem

### Questions
* how to run large scale failure tests?
* what are abort conditions?
* how to communicate? let people know failure test is * happening

### post mordem
* did it work as expected?
* did find bugs? if found bugs may want to try again in a couple weeks to make sure bugs were fixed
* automate tests if found

### metrics
* what's top key metric
* eg at amazon, can people order
* netflix can people stream

#### service metrics
* is api working
* has there been a throughput change
* what does load look like
* individual boxes

### trace infrastructure
* https://research.google.com/pubs/pub36356.html
* https://dzone.com/articles/peek-google%E2%80%99s-production