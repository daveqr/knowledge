# Continuous Delivery

## Testing
* test from top to bottom
* functional tests
* test the most improotant customer-focused workflow first
* user-driven testing
* functional tests 
  * larger tests
  *  feature works, not just the code
  *  eg login
  *  Selenium
  *  start with a happy path test
  *  then write a sad path
  *  use unit test for more detailed testing
  *  don't need to test everything in functional test
    *  eg form submission
    *  test submit and choose a field to test
    *  use unit testing for all other fields
* integration tests
  * workflow for services
  * technology focused
  * might use selenium to kick off
* write more functional tests early, testing the user's workflow

## Deploys
* goal is to not think about deploys
* merge code into a branch and don't think about it
* get a notification that the deploy succeeded or failed
* how to do this? merge from 1 branch to another and everything gets triggered
* can manually trigger by moving to branch
  * eg master or 'prod' branch
* test infrastructure
* release easily
* most paeople use factories to load data for DB tests
* goal should be 2-3 min build
  * this is the sweet-spot for not thinking about the result
  * get feedback right when we start to think about it
  * if longer than 2-3 minutes, you start to think did that build work?