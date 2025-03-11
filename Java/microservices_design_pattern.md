## Microservices design pattern
it's concept to resolve daily occuring problem during microservice deployment.
1. API gateway: first entry point, redirect as per rule
2. database per ser design pattern: every microservice has a single DB
3. service discovery: to connect internal endpoint
4. circuit breaker: it any system is failing countinously open the circuit and redirect the fail msg  
5. saga design pattern - cherography design pattern, orchestraction design pattern
6. event sourcing
7. cqrs(command query responsbility segregation)
8. stranger fig pattern : in process of migration monolathic app to microservice, slowly divided balance to new microservice percentage wise, to reduce the risk
9. proxy design pattern: add a extra leyer like API gateway, for monitor, logging and security purpose
10. Bulkhead: separate all endpoint to work as independly  
11. compensation transaction pattern: it used in saga design pattern, while roll back
12. decomposition : in process of migration of microservice, devide big app in small part and develope, help in migration.



### Saga Design pattern: 
when disturbuted sys come in picture then Saga come in picture, this design has capability to rollback. 
if a take an example of ecommerce system with monolathic system, it's tight couple system like first oreder, second payment confirmation, third delievry sys, four delivery confirmation. this is syncnaze way or chain sys. if anything process fail, full sys will fail. even we migrate to microservice then all endpoint not work independly due to tight couple.
so Saga design comes in the picture. if something is failed the sys can roll back or reperforme here.
we can achive by two way

### 1.cherography: 
as name suggest it'll suggest direction by using event emitting sys and make app service indpendent. 
adavnatage: no need to write additional code, simple
Disadvantage: it'll unable to handle complex work if multiple msg comes at same time

e.g 
order service   ->
payment service  -> message emmitter   -> client
delivery service ->


### Orchestration:
same as cherography but able to handle complex mupltiple process at a time, it handle as centrilize way, commanding all services.
Disadvantage: it's tight couple because working as centralize way, need to write code mean need extra effort to implement. if this sys fail, sys won't work.

## Event sorcing/event emitter:
For every transaction, it'll create a event so it'll eassy to see the history and if fail then recap and fix the issue. means easy to debug and loosly coupled.
e.g: 
order create-> create a event
payment confirmation -> create a event
noticication -> nofity user, hotel and delivery boy
if anything fail we can rollback.


## CQRS: command query responsibilty segragation 
Command(read) and Query(write), here we are divinding into two DB, one for insertion/updatation like RDBMS, second for reading purpose like NoSQL. due to for insertion, inserting many confidential info like SSN, ADHAR, full details. but for view pupose we don't need full info just summary is good.
internally one event bus like azure bus to sync two DB. 





      
