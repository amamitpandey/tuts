# Type of testing in java

## Pyramid top to bottom
* Smoke test
* Performance testing
* contract test
* acceptance test
* Regression testing
* integration test 
* Unit test

1. Smoke test:  this term comes from electronic/plumbing, if you can't see smoke then it's fine for another level of testing.
   it's saved tester's time, so just need to test response is ok or not.  
2. Performance testing: testing under certain workload like calling an Api 100 times at a time

3. Contract test:  it's a relation between producer and consumer. The goal is making sure request object and response object as   per contract(like mention in groovy file). If developer modifies any object, contract will compliance at side of consumer and        notify them to update their code. 

4. Regression testing: after adding a new module, need to verify, completely application is working fine or not.

5. Acceptance testing: it's try to run complete app, even external and internal class/method/calls. do not mock any thing. It's expensive than integration and takes more time. 

6. Integration test: as name suggests it'll test all level of interface, only internal, like services, controller, repository and DB. One test can test all part. it's called all application context using some spring annotation - "@autoconfigurationMockmvc, @springboottest(...) @jpatest"  even we have some more annotation for integration test.
We can insert data without using any api call. It'll auto test all layer like calling a single Api like bean to db. We should be mock bean for this.
we mock external or some method where we don't want to check.

// for setup Environment variables
System.setProperty("java.runtime.version", "Java Runtime 1.6.0");
ReflectionTestUtils.setField(employee, "id",1); // used in junit and integration
// for spring batch
Need to test job, step execution, file read, write things
@extendwith
@springboottest
@enablebatchprocessing
@contextconfiguration
@testexecutionlisteners
@dirtiescontext
@Activeprofiles


7. Unit test: as name suggest unit, it's test, small piece of code. let's says if we want to test an API, we need separate piece of code for bean, controller, repo and DB for each one, otherwise it's want cover sonar coverage. but in integration test one test do all thing its own.  It's called a single context of application and mock many times. data's are not real.

Mocking: use for a complex object, external things. it's try copy like real thing and replace with fake object. Mocking means we are declaring a duplicate like method, service etc. and guide what could be output if this method called without calling that method.

BDD: Behavior driven development, is a idea use test in a simple way like //given..//when...//then. it's combo of tdd and genaral techniech.
TDD: Test driven development, idea is first write test and pass it later by writing the code, it's a agile pratice.

Stubing: means use minimal/ignore steps many thing like we use fake like jwt token.
