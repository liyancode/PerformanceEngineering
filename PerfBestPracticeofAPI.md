# API Performance Test best practice

1. Test Environment Preparation  
In most cases, performance testing does not touch production directly instead of pre-production or specific performance testing environment. So before starting test, please try best to make that all of the changes and configurations are consisted with what they will be in production, which sometimes is hard to ensured(hardware resources limited, etc.), but at least ensure these important configurations. Here is a checklist for reference, including but not limited to:
1) API code and dependency code version. \[important]
2) Application server software configuration(e.g. JVM configuration of Java App). \[important]
3) Application server hardware configuration: VM or Physical machine, CPU/Memory/Disk/Network,etc. If it is hard to get the same count of production servers, please make sure that the key path servers count at the same ratio(e.g. app_A:app_B=2:1). \[important]
4) Database. Mostly should not be the bottleneck.
5) Network. It is best to let the test client and the app servers at the same network domain, which can maximally eliminate the overhead from network communication. BTW, make sure the network layer load balancer run the same strategy.
6) 3rd party service environment which is out of control. If depending on 3rd party service(e.g. pay api), please make sure your testing will not crash them, and if possible just mock or bypass it.
7) No noise. Make sure there is no other testings happen at the same environment during your test. \[important]


2. Test Cases Choose  
Performance test is not equal to looped/concurrent function test. 
....
